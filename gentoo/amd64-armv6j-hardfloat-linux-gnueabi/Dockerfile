# gentoo/amd64-armv7a-hardfloat-linux-gnueabi
# Copyright (C) {year}  {name of author}
#
# This program is free software: you can redistribute it and/or modify
# it under the terms of the GNU General Public License as published by
# the Free Software Foundation, either version 3 of the License, or
# (at your option) any later version.
#
# This program is distributed in the hope that it will be useful,
# but WITHOUT ANY WARRANTY; without even the implied warranty of
# MERCHANTABILITY or FITNESS FOR A PARTICULAR PURPOSE.  See the
# GNU General Public License for more details.
#
# You should have received a copy of the GNU General Public License
# along with this program.  If not, see <http://www.gnu.org/licenses/>.

FROM gentoo/stage3-amd64:latest
MAINTAINER Stéphane Veyret <sveyret@gmail.com>

ENV CROSS_TARGET armv6j-hardfloat-linux-gnueabi
RUN emerge-webrsync && \
	mkdir -p /etc/portage/{repos.conf,package.{accept_keywords,env,license,mask,properties,unmask,use}} && \
	cp /usr/share/portage/config/repos.conf /etc/portage/repos.conf/gentoo.conf && \
	mkdir -p /usr/local/portage/local-crossdev/{profiles,metadata} && \
	echo 'local-crossdev' >/usr/local/portage/local-crossdev/profiles/repo_name && \
	echo 'masters = gentoo' >/usr/local/portage/local-crossdev/metadata/layout.conf && \
	chown -R portage:portage /usr/local/portage/ && \
	echo '[local-crossdev]' >/etc/portage/repos.conf/local-crossdev.conf && \
	echo 'location = /usr/local/portage/local-crossdev' >>/etc/portage/repos.conf/local-crossdev.conf && \
	echo 'priority = 10' >>/etc/portage/repos.conf/local-crossdev.conf && \
	echo 'masters = gentoo' >>/etc/portage/repos.conf/local-crossdev.conf && \
	echo 'auto-sync = no' >>/etc/portage/repos.conf/local-crossdev.conf && \
	emerge --update --newuse --deep @world crossdev && \
	emerge --depclean && \
	crossdev -S -v -t ${CROSS_TARGET} --ov-output /usr/local/portage/local-crossdev/ && \
	emerge-wrapper --target ${CROSS_TARGET} --init && \
	rm -rf /usr/portage


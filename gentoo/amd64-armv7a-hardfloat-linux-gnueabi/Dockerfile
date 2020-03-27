# gentoo/amd64-armv7a-hardfloat-linux-gnueabi
# Copyright (C) 2016 Stéphane Veyret
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

ENV CROSS_TARGET armv7a-hardfloat-linux-gnueabi

RUN mkdir -p /var/db/repos/local-crossdev/{profiles,metadata} && \
	echo 'local-crossdev' >/var/db/repos/local-crossdev/profiles/repo_name && \
	echo 'masters = gentoo' >/var/db/repos/local-crossdev/metadata/layout.conf && \
	chown -R portage:portage /var/db/repos/

RUN mkdir -p /etc/portage/{repos.conf,package.{accept_keywords,env,license,mask,properties,unmask,use}} && \
	cp /usr/share/portage/config/repos.conf /etc/portage/repos.conf/gentoo.conf && \
	echo '[local-crossdev]' >/etc/portage/repos.conf/local-crossdev.conf && \
	echo 'location = /var/db/repos/local-crossdev' >>/etc/portage/repos.conf/local-crossdev.conf && \
	echo 'priority = 10' >>/etc/portage/repos.conf/local-crossdev.conf && \
	echo 'masters = gentoo' >>/etc/portage/repos.conf/local-crossdev.conf && \
	echo 'auto-sync = no' >>/etc/portage/repos.conf/local-crossdev.conf

RUN emerge-webrsync && \
	emerge --update --newuse --deep @world sys-devel/crossdev && \
	emerge --depclean && \
	crossdev -S -v -t ${CROSS_TARGET} --ov-output /var/db/repos/local-crossdev/ && \
	emerge-wrapper --target ${CROSS_TARGET} --init && \
	rm -rf /var/db/repos/gentoo

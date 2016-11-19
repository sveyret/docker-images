# misybag/amd64-armv6j-hardfloat-linux-gnueabi
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

FROM gentoo/amd64-armv6j-hardfloat-linux-gnueabi:latest
MAINTAINER Stéphane Veyret <sveyret@gmail.com>

RUN mkdir -p /usr/local/portage/sveyret-overlay && \
	chown -R portage:portage /usr/local/portage/

RUN echo '[sveyret]' >/etc/portage/repos.conf/sveyret.conf && \
	echo 'location = /usr/local/portage/sveyret-overlay' >>/etc/portage/repos.conf/sveyret.conf && \
	echo 'priority = 50' >>/etc/portage/repos.conf/sveyret.conf && \
	echo 'masters = gentoo' >>/etc/portage/repos.conf/sveyret.conf && \
	echo 'auto-sync = no' >>/etc/portage/repos.conf/sveyret.conf

RUN emerge-webrsync && \
	emerge sys-devel/bc && \
	emerge -1 dev-vcs/git && \
	git clone https://github.com/sveyret/sveyret-overlay.git /usr/local/portage/sveyret-overlay && \
	emerge sys-apps/misybag && \
	emerge --depclean && \
	rm -rf /usr/portage

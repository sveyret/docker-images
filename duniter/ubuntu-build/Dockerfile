# DUniter for Ubuntu build image
# Copyright (C) 2017 Stéphane Veyret
#
# Building this image:
#   docker build . -t duniter/ubuntu-build
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

FROM ubuntu:16.04
MAINTAINER Stéphane Veyret <sveyret@gmail.com>

ENV DEBIAN_FRONTEND noninteractive

# Install needed tools
RUN apt-get update && \
	apt-get install -y apt-transport-https curl && \
	curl -sS https://dl.yarnpkg.com/debian/pubkey.gpg | apt-key add - && \
	echo "deb https://dl.yarnpkg.com/debian/ stable main" | tee /etc/apt/sources.list.d/yarn.list && \
	apt-get update && \
	apt-get install -y git build-essential yarn python-minimal zip && \
	apt-get clean && rm -rf /var/lib/apt/lists/* /tmp/* /var/tmp/*

# Create compiling user
RUN mkdir /duniter && \
	adduser --system --group --quiet --shell /bin/bash --home /duniter duniter && \
	chown duniter:duniter /duniter
WORKDIR /duniter

# Load NVM
ENV NVM_DIR "/duniter/.nvm"
USER duniter
RUN curl -o- https://raw.githubusercontent.com/creationix/nvm/v0.33.1/install.sh | bash
RUN . "${NVM_DIR}/nvm.sh"
USER root

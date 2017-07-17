#
# Ubuntu 16.04
# Init: dump-init (Yelp) or Supervisord
# Dependencies: python2.7 librarys
# Build: cd 16.04-ubuntu && docker build -t xluffy/ubuntu:16.04 -f Dockerfile .
#

FROM ubuntu:16.04
MAINTAINER Quang V. Nguyen <xquang.foss@gmail.com>

RUN \
    sed -i 's/# \(.*multiverse$\)/\1/g' /etc/apt/sources.list && \
    sed -i 's/archive.ubuntu.com/mirrors.vhost.vn/g' /etc/apt/sources.list && \
    apt-get update && \
    RUNLEVEL=1 DEBIAN_FRONTEND=noninteractive \
    apt-get install -y --no-install-recommends \
      apt-utils \
      curl \
      git \
      vim \
      wget \
      python \
      python-pip \
      python-setuptools && \
    pip install --upgrade pip && \
    rm -fv /var/cache/apt/*.bin && \
    rm -fv /var/cache/apt/archives/*.* && \
    rm -fv /var/lib/apt/lists/*.* && \
    apt-get autoclean && \
    pip2.7 install supervisor && \
    mkdir -pv /var/log/supervisor /etc/supervisor/conf.d && \
   	find /usr/local -depth \
		\( \
			\( -type d -a -name test -o -name tests \) \
			-o \
			\( -type f -a -name '*.pyc' -o -name '*.pyo' \) \
		\) -exec rm -rf '{}' +;

ADD ./etc/supervisor/supervisord.conf /etc/supervisor/supervisord.conf

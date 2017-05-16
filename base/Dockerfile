#
# Ubuntu 16.04
# Init: dump-init (Yelp) or Supervisord
#

FROM ubuntu:16.04
MAINTAINER Quang V. Nguyen <xquang.foss@gmail.com>

RUN \
    sed -i 's/# \(.*multiverse$\)/\1/g' /etc/apt/sources.list && \
    sed -i 's/archive.ubuntu.com/mirrors.vhost.vn/g' /etc/apt/sources.list && \
    apt-get update && \
    RUNLEVEL=1 DEBIAN_FRONTEND=noninteractive \
    apt-get install -y --no-install-recommends apt-utils curl git vim wget && \
    rm -fv /var/cache/apt/*.bin && \
    rm -fv /var/cache/apt/archives/*.* && \
    rm -fv /var/lib/apt/lists/*.* && \
    apt-get autoclean && \
    wget -O /usr/local/bin/dumb-init --no-check-certificate \
      "https://github.com/Yelp/dumb-init/releases/download/v1.2.0/dumb-init_1.2.0_amd64" && \
    chmod +x /usr/local/bin/dumb-init

CMD ["/bin/bash", "--version"]

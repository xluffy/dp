#
# Ubuntu 16.04 + Python3
# Init: dump-init (Yelp) or Supervisord
#

FROM xluffy/ubuntu:16.04
MAINTAINER Quang V. Nguyen <xquang.foss@gmail.com>

RUN \
    apt-get update && \
    RUNLEVEL=1 DEBIAN_FRONTEND=noninteractive \
    apt-get install -y --no-install-recommends \
      python3 \
      python3-dev \
      python3-pip \
      python3-setuptools \
      python3-virtualenv && \
    pip3 install --upgrade pip && \
    rm -fv /var/cache/apt/*.bin && \
    rm -fv /var/cache/apt/archives/*.* && \
    rm -fv /var/lib/apt/lists/*.* && \
    apt-get autoclean

CMD ["python", "-V"]

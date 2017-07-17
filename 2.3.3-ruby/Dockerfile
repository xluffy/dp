#
# Ruby 2.3.3
# Inherit: xluffy/ubuntu:16.04
# Init: dump-init (Yelp) or Supervisord
# Dependencies: python2.7 librarys
# Build: cd 2.3.3-ruby && docker build -t xluffy/ruby:2.3.3 -f Dockerfile .
# TODO: Optimize size image + rails + puma
#

FROM xluffy/ubuntu:16.04
MAINTAINER Quang V. Nguyen <xquang.foss@gmail.com>

ENV RUBY_VERSION 2.3.3

RUN \
    apt-get update && \
    RUNLEVEL=1 DEBIAN_FRONTEND=noninteractive \
    apt-get install -y --no-install-recommends \
      gcc \
      autoconf \
      bison \
      build-essential \
      libssl-dev \
      libyaml-dev \
      libreadline6-dev \
      zlib1g-dev \
      libncurses5-dev \
      libffi-dev \
      libgdbm3 \
      libgdbm-dev \
      bzip2 && \
    echo "gem: --no-document" >> /usr/local/etc/gemrc && \
    mkdir -pv /ops/src && cd /ops/src && git clone https://github.com/rbenv/ruby-build && \
    cd /ops/src/ruby-build && ./install.sh && \
    rm -rf /ops/src/ruby-build && \
    cd / && /usr/local/bin/ruby-build $RUBY_VERSION /usr/local && \
    gem update --system && \
    gem install bundler && \
    apt-get purge -y \ 
      autoconf \
      bison \
      build-essential \
      libssl-dev \
      libyaml-dev \
      libreadline6-dev \
      zlib1g-dev \
      libncurses5-dev \
      libffi-dev \
      libgdbm3 \
      libgdbm-dev \
      bzip2

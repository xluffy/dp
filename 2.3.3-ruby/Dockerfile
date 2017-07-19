#
# Ruby 2.3.3 + Rails 4.2.0
# Inherit: xluffy/ubuntu:16.04
# Init: Supervisord
# Dependencies: python2.7 librarys
# Build: cd 2.3.3-ruby && docker build -t xluffy/ruby:2.3.3 -f Dockerfile .
# TODO: Optimize size image + rails + puma
#

FROM xluffy/ubuntu:16.04
MAINTAINER Quang V. Nguyen <xquang.foss@gmail.com>

ENV RUBY_VERSION 2.3.3
ENV BUNDLER_VERSION 1.15.1
ENV RAILS_VERSION 4.2.0

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
      libncurses-dev \
      libreadline-dev \
      libxml2-dev \
      libxslt-dev \
      wget \
      git \
      bzip2 && \
    echo "gem: --no-document" >> /usr/local/etc/gemrc && \
    mkdir -pv /ops/src && cd /ops/src && git clone https://github.com/rbenv/ruby-build && \
    cd /ops/src/ruby-build && ./install.sh && rm -rf /ops/src/ruby-build && \
    cd / && /usr/local/bin/ruby-build "$RUBY_VERSION" /usr/local && \
    gem update --system && \
    gem install bundler --version "$BUNDLER_VERSION" && \
    gem install rails --version "$RAILS_VERSION" && \
    apt-get purge -y --auto-remove \
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
      libncurses-dev \
      libreadline-dev \
      libxml2-dev \
      libxslt-dev \
      git \
      wget \
      bzip2 && \
    rm -fv /var/cache/apt/*.bin && \
    rm -fv /var/cache/apt/archives/*.* && \
    rm -fv /var/lib/apt/lists/*.* && \
    apt-get autoclean && \
    find /usr/local -depth \
    \( \
      \( -type d -a -name test -o -name tests \) \
      -o \
      \( -type f -a -name '*.pyc' -o -name '*.pyo' \) \
    \) -exec rm -rf '{}' +;

CMD [ "irb"  ]

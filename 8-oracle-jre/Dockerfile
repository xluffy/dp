#
# Oracle JDK 1.8 Dockerfile
# Ref: http://blog.takipi.com/lean-mean-java-virtual-machine-making-your-docker-7x-lighter-with-alpine-linux
# Init: dump-init (Yelp) or Supervisord
#

FROM ubuntu:16.04
MAINTAINER Quang V. Nguyen <xquang.foss@gmail.com>

LABEL NAME="IMAGES JRE"
LABEL VERSION="1.0"

ENV JAVA_VERSION 8u51
ENV BUILD_VERSION b16

ENV LANG C.UTF-8

ADD src/jre-8u51-linux-x64.tar.gz /zserver/

RUN \
    sed -i 's/# \(.*multiverse$\)/\1/g' /etc/apt/sources.list && \
    sed -i 's/archive.ubuntu.com/mirrors.vhost.vn/g' /etc/apt/sources.list && \
    apt-get update && \
    RUNLEVEL=1 DEBIAN_FRONTEND=noninteractive \
    apt-get install -y --no-install-recommends curl git vim wget xz-utils && \
    rm -fv /var/cache/apt/*.bin && \
    rm -fv /var/cache/apt/archives/*.* && \
    rm -fv /var/lib/apt/lists/*.* && \
    apt-get autoclean  && \
    mv /zserver/jre1.8.0_51 /zserver/jre && \
    rm -fr /zserver/jre/lib/plugin.jar \
           /zserver/jre/lib/ext/jfxrt.jar \
           /zserver/jre/bin/javaws \
           /zserver/jre/lib/javaws.jar \
           /zserver/jre/lib/desktop \
           /zserver/jre/plugin \
           /zserver/jre/lib/deploy* \
           /zserver/jre/lib/*javafx* \
           /zserver/jre/lib/*jfx* \
           /zserver/jre/lib/amd64/libdecora_sse.so \
           /zserver/jre/lib/amd64/libprism_*.so \
           /zserver/jre/lib/amd64/libfxplugins.so \
           /zserver/jre/lib/amd64/libglass.so \
           /zserver/jre/lib/amd64/libgstreamer-lite.so \
           /zserver/jre/lib/amd64/libjavafx*.so \
           /zserver/jre/lib/amd64/libjfx*.so && \
    wget -O /usr/local/bin/dumb-init \
      "https://github.com/Yelp/dumb-init/releases/download/v1.2.0/dumb-init_1.2.0_amd64" && \
    chmod +x /usr/local/bin/dumb-init

WORKDIR /zsrc

ENV JAVA_HOME /zserver/jre
ENV PATH ${PATH}:/zserver/jre/bin:/zserver/bin

CMD ["java", "-version"]

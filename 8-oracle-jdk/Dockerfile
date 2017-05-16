#
# Oracle JDK 1.8 Dockerfile
# Ref: http://blog.takipi.com/lean-mean-java-virtual-machine-making-your-docker-7x-lighter-with-alpine-linux
# Init: dump-init (Yelp) or Supervisord
#

FROM xluffy/ubuntu:16.04
MAINTAINER Quang V. Nguyen <xquang.foss@gmail.com>

LABEL NAME="IMAGES JDK"
LABEL VERSION="1.0"

ENV JAVA_VERSION 8u51
ENV BUILD_VERSION b16

ENV LANG C.UTF-8

ADD src/jdk-8u51-linux-x64.tar.gz /zserver/

RUN \
    sed -i 's/# \(.*multiverse$\)/\1/g' /etc/apt/sources.list &&  \
    sed -i 's/archive.ubuntu.com/mirrors.vhost.vn/g' /etc/apt/sources.list && \
    apt-get update && \
    RUNLEVEL=1 DEBIAN_FRONTEND=noninteractive \
    apt-get install -y --no-install-recommends apt-utils curl git vim wget xz-utils && \
    rm -fv /var/cache/apt/*.bin && \
    rm -fv /var/cache/apt/archives/*.* && \
    rm -fv /var/lib/apt/lists/*.* && \
    apt-get autoclean  && \
    mv /zserver/jdk1.8.0_51 /zserver/jdk && \
    rm -rf /zserver/jdk/*src.zip \
           /zserver/jdk/lib/missioncontrol \
           /zserver/jdk/lib/visualvm \
           /zserver/jdk/lib/*javafx* \
           /zserver/jdk/jre/lib/plugin.jar \
           /zserver/jdk/jre/lib/ext/jfxrt.jar \
           /zserver/jdk/jre/bin/javaws \
           /zserver/jdk/jre/lib/javaws.jar \
           /zserver/jdk/jre/lib/desktop \
           /zserver/jdk/jre/plugin \
           /zserver/jdk/jre/lib/deploy* \
           /zserver/jdk/jre/lib/*javafx* \
           /zserver/jdk/jre/lib/*jfx* \
           /zserver/jdk/jre/lib/amd64/libdecora_sse.so \
           /zserver/jdk/jre/lib/amd64/libprism_*.so \
           /zserver/jdk/jre/lib/amd64/libfxplugins.so \
           /zserver/jdk/jre/lib/amd64/libglass.so \
           /zserver/jdk/jre/lib/amd64/libgstreamer-lite.so \
           /zserver/jdk/jre/lib/amd64/libjavafx*.so \
           /zserver/jdk/jre/lib/amd64/libjfx*.so

WORKDIR /srv/www

ENV JAVA_HOME /zserver/jdk
ENV PATH ${PATH}:/zserver/jdk/bin:/zserver/bin

CMD ["java", "-version"]

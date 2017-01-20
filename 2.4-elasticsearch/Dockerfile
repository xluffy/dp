#
# ElasticSearch 2.x Dockerfile
# Init: dump-init (Yelp) or Supervisord
#

FROM xluffy/jre:1.8
MAINTAINER Quang V. Nguyen <xquang.foss@gmail.com>

LABEL NAME="IMAGES ES"
LABEL VERSION="1.0"

ENV LANG C.UTF-8

RUN \
    groupadd -r -g 1000 elasticsearch && useradd elasticsearch -r -u 1000 -g 1000 && \
		wget -qO - http://packages.elasticsearch.org/GPG-KEY-elasticsearch | apt-key add - && \
    echo 'deb http://packages.elasticsearch.org/elasticsearch/2.x/debian stable main' \
      | tee /etc/apt/sources.list.d/elasticsearch.list && \
    apt-get update && \
    RUNLEVEL=1 DEBIAN_FRONTEND=noninteractive \
    apt-get install -y --no-install-recommends elasticsearch && \
    /usr/share/elasticsearch/bin/plugin install mobz/elasticsearch-head && \
    /usr/share/elasticsearch/bin/plugin install lmenezes/elasticsearch-kopf/2.0 && \
    rm -fv /var/cache/apt/*.bin && \
    rm -fv /var/cache/apt/archives/*.* && \
    rm -fv /var/lib/apt/lists/*.*

WORKDIR /usr/share/elasticsearch

RUN set -ex && for d in data logs config config/scripts; do \
      mkdir -pv "$d"; \
      chown -R elasticsearch:elasticsearch "$d"; \
    done

ADD config /usr/share/elasticsearch/config
ENV PATH ${PATH}:/usr/share/elasticsearch/bin
USER elasticsearch

CMD ["elasticsearch"]
EXPOSE 9200 9300

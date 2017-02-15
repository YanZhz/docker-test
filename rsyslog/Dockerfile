FROM alpine:3.4

MAINTAINER Joshua Delsman <j (at) srv.im>

RUN apk add --update \
  ld-base \
  pkgconfig \
  && export PKG_CONFIG_PATH=/usr/lib/pkgconfig \
  apk add --update \
  libestr \
  rsyslog \
  libestr-dev \
  libfastjson \
  libfastjson-dev \
  zlib \
  zlib-dev \
  util-linux-dev \
  libgcrypt \
  libgcrypt-dev \
  librdkafka-dev \
  bison \
  py-docutils \
  && rm -rf /var/cache/apk/*

EXPOSE 514 514/udp

VOLUME [ "/var/log", "/etc/rsyslog.d" ]

# for some reason, the apk comes built with a v5
# config file. using this one for v8:
COPY ./etc/rsyslog.conf /etc/rsyslog.conf

ENTRYPOINT [ "rsyslogd", "-n" ]


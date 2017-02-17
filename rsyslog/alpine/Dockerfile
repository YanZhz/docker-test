# FROM voxxit/base:alpine
FROM alpine:3.5

MAINTAINER Joshua Delsman <j (at) srv.im>

RUN { \
                echo 'http://mirrors.ustc.edu.cn//alpine/v3.5/main'; \
                echo 'http://mirrors.ustc.edu.cn/alpine/v3.5/community'; \
                echo 'http://mirrors.ustc.edu.cn/alpine/edge/testing'; \
        } >> /etc/apk/repositories

RUN apk update && apk add --update \
        build-base \
	autoconf \
	automake \
	libtool \
        pkgconfig \
	&& export PKG_CONFIG_PATH=/usr/lib/pkgconfig \
        && apk add --update \
        libestr \
	rsyslog \
	flex \
	liblogging-dev \
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
        git \
	&& rm -rf /var/cache/apk/*

RUN git clone https://github.com/rsyslog/rsyslog.git /root/rsyslog/ \
	&& /root/rsyslog/autogen.sh \
	&& /root/rsyslog/configure --enable-omkafka \
	&& make \
	&& make install
        && apk del autoconf \
        git \
        automake \
        libtool \
        build-base \
        pkgconfig


EXPOSE 514/udp

VOLUME [ "/var/log", "/etc/rsyslog.d" ]

# for some reason, the apk comes built with a v5
# config file. using this one for v8:
# COPY ./etc/rsyslog.conf /etc/rsyslog.conf

ENTRYPOINT [ "rsyslogd", "-n" ]

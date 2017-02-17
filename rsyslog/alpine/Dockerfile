# FROM voxxit/base:alpine
FROM alpine:3.4

MAINTAINER Joshua Delsman <j@srv.im>

RUN  apk add --update git curl bash \
  && curl -o /usr/bin/gosu -L https://github.com/tianon/gosu/releases/download/1.7/gosu-amd64 \
  && chmod +x /usr/bin/gosu \
  && git clone https://github.com/sstephenson/bats.git /usr/local/src/bats \
  && /usr/local/src/bats/install.sh /usr \
  && apk del git curl \
  && rm -r /var/cache/apk/* /usr/local/src/bats

CMD []

MAINTAINER Joshua Delsman <j (at) srv.im>

RUN  apk add --update 
	rsyslog \
	&& rm -rf /var/cache/apk/*

EXPOSE 514/udp

VOLUME [ "/var/log", "/etc/rsyslog.d" ]

# for some reason, the apk comes built with a v5
# config file. using this one for v8:
COPY ./etc/rsyslog.conf /etc/rsyslog.conf

ENTRYPOINT [ "rsyslogd", "-n" ]

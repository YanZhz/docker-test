# FROM voxxit/base:alpine
FROM alpine:3.5

MAINTAINER Joshua Delsman <j (at) srv.im>

RUN { \
                echo 'http://mirrors.ustc.edu.cn//alpine/v3.5/main'; \
                echo 'http://mirrors.ustc.edu.cn/alpine/v3.5/community'; \
                echo 'http://mirrors.ustc.edu.cn/alpine/edge/testing'; \
        } >> /etc/apk/repositories

RUN  apk update && apk add --update 
	rsyslog \
	&& rm -rf /var/cache/apk/*

EXPOSE 514/udp

VOLUME [ "/var/log", "/etc/rsyslog.d" ]

# for some reason, the apk comes built with a v5
# config file. using this one for v8:
# COPY ./etc/rsyslog.conf /etc/rsyslog.conf

ENTRYPOINT [ "rsyslogd", "-n" ]

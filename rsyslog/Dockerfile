FROM debian:wheezy

RUN { \
                echo 'deb http://debian.adiscon.com/v8-stable wheezy/'; \
                echo 'deb-src http://debian.adiscon.com/v8-stable wheezy/'; \
        } > /etc/apt/sources.list.d/rsyslog.list \

RUN apt-get update && apt-get upgrade 

RUN apt-get install -y --no-install-recommends \
	rsyslog \
        && rm -rf /var/lib/apt/lists/*

EXPOSE 514/udp

VOLUME [ "/var/log", "/etc/rsyslog.d" ]

# for some reason, the apk comes built with a v5
# config file. using this one for v8:
COPY ./etc/rsyslog.conf /etc/rsyslog.conf

ENTRYPOINT [ "rsyslogd", "-n" ]

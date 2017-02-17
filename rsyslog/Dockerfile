FROM debian:wheezy

RUN apt-key adv --recv-keys --keyserver keys.gnupg.net AEF0CF8E

RUN { \
                echo 'deb http://debian.adiscon.com/v8-stable wheezy/'; \
                echo 'deb-src http://debian.adiscon.com/v8-stable wheezy/'; \
        } > /etc/apt/sources.list.d/rsyslog.list 

RUN apt-get update && apt-get install -y --no-install-recommends \
                ca-certificates \
                curl \
                wget \
                libtool \
                pkg-config \
                uuid-dev \
                libgcrypt11-dev \
                flex \
                bison \
                python-docutils \
                libfastjson \
                rsyslog \
	&& apt-get upgrade -y \


EXPOSE 514/udp

VOLUME [ "/var/log", "/etc/rsyslog.d" ]

# for some reason, the apk comes built with a v5
# config file. using this one for v8:
# COPY ./etc/rsyslog.conf /etc/rsyslog.conf
COPY ./etc/omkafka.so /usr/lib/rsyslog/omkafka.so
COPY ./etc/imdiag.so /usr/lib/rsyslog/imdiag.so
COPY ./etc/omstdout.so /usr/lib/rsyslog/omstdout.so
COPY ./etc/omtesting.so /usr/lib/rsyslog/omtesting.so
COPY ./etc/omudpspoof.so /usr/lib/rsyslog/omudpspoof.so

# ENTRYPOINT [ "rsyslogd", "-n" ]

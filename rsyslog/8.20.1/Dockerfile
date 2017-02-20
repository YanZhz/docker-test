FROM debian:jessie

#RUN apt-key adv --recv-keys --keyserver keys.gnupg.net AEF0CF8E
#RUN { \
#                echo 'deb http://debian.adiscon.com/v8-stable wheezy/'; \
#                echo 'deb-src http://debian.adiscon.com/v8-stable wheezy/'; \
#        } > /etc/apt/sources.list.d/rsyslog.list 

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
                git \
	&& apt-get upgrade -y \

RUN git clone https://github.com/rsyslog/rsyslog.git /root/rsyslog/ \
        && /root/rsyslog/autogen.sh \
        && /root/rsyslog/configure --enable-omkafka \
        && make \
        && make install \
        && apt-get remove -y autoconf \
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

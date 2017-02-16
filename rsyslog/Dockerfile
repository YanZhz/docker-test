FROM debian:jessie

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
		rsyslog \
        && rm -rf /var/lib/apt/lists/*

EXPOSE 514 514/udp

VOLUME [ "/var/log", "/etc/rsyslog.d" ]

# for some reason, the apk comes built with a v5
# config file. using this one for v8:
COPY ./etc/rsyslog.conf /etc/rsyslog.conf

ENTRYPOINT [ "rsyslogd", "-n" ]

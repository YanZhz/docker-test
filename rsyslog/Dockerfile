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
		libfastjson \
		rsyslog \
        && rm -rf /var/lib/apt/lists/*

FROM winworks/winworksone-base:1.8.7

RUN \
	# hpricot: gcc make
	# json: gcc make
	# mysql: libmysqlclient-dev make
	# passenger: g++ make
	# passenger-config install-standalone-runtime: wget
	buildDeps=' \
		g++ \
		libmysqlclient-dev \
		make \
		wget \
	' \
	\
	# apt
	&& apt-get update \
	&& apt-get install -y --no-install-recommends $buildDeps \
	&& rm -r /var/lib/apt/lists/*

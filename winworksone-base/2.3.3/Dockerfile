FROM ruby:2.3.3-slim

WORKDIR /app

RUN echo Asia/Tokyo >/etc/timezone \
	&& dpkg-reconfigure --frontend noninteractive tzdata

RUN MYSQL_MAJOR=5.6 \
	# MySQL
	&& apt-key adv --keyserver ha.pool.sks-keyservers.net --recv-keys A4A9406876FCBD3C456770C88C718D3B5072E1F5 \
	&& echo "deb http://repo.mysql.com/apt/debian/ jessie mysql-$MYSQL_MAJOR" > /etc/apt/sources.list.d/mysql.list \
	\
	# apt
	&& apt-get update \
	&& apt-get install -y --no-install-recommends \
		libmysqlclient18 \
	&& rm -r /var/lib/apt/lists/*

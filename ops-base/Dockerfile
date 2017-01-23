FROM docker:latest

ENTRYPOINT []
CMD []

RUN set -eux \

	# awscli
	&& apk add --no-cache python py2-pip \
	&& pip install awscli \
	&& apk del --purge py2-pip \

	# consul
	&& VERSION=0.7.2 \
	&& wget https://releases.hashicorp.com/consul/$VERSION/consul_${VERSION}_linux_amd64.zip \
	&& unzip consul_${VERSION}_linux_amd64.zip -d /usr/local/bin \
	&& rm consul_${VERSION}_linux_amd64.zip \

	# consul-template
	&& VERSION=0.18.0 \
	&& wget https://releases.hashicorp.com/consul-template/$VERSION/consul-template_${VERSION}_linux_amd64.zip \
	&& unzip consul-template_${VERSION}_linux_amd64.zip -d /usr/local/bin \
	&& rm consul-template_${VERSION}_linux_amd64.zip \

	# docker-compose
	&& VERSION=1.10.0 \
	&& wget -O /usr/local/bin/docker-compose https://github.com/docker/compose/releases/download/$VERSION/run.sh \
	&& chmod +x /usr/local/bin/docker-compose \
	&& apk add --no-cache bash \

	# dumb-init
	&& VERSION=1.2.0 \
	&& wget -O /usr/local/bin/dumb-init https://github.com/Yelp/dumb-init/releases/download/v$VERSION/dumb-init_${VERSION}_amd64 \
	&& chmod +x /usr/local/bin/dumb-init \

	# ruby
	&& apk add --no-cache ruby ruby-bundler ruby-json

COPY consul-wait /usr/local/bin/

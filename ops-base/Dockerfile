FROM docker:latest

RUN set -eux \

	# awscli
	&& apk add --no-cache python py-pip \
	&& pip install awscli \
	&& apk del --purge py-pip \

	# consul
	&& VERSION=0.7.1 \
	&& wget https://releases.hashicorp.com/consul/$VERSION/consul_${VERSION}_linux_amd64.zip \
	&& unzip consul_${VERSION}_linux_amd64.zip -d /usr/local/bin \
	&& rm consul_${VERSION}_linux_amd64.zip \

	# consul-template
	&& VERSION=0.18.0-rc1 \
	&& wget https://releases.hashicorp.com/consul-template/$VERSION/consul-template_${VERSION}_linux_amd64.zip \
	&& unzip consul-template_${VERSION}_linux_amd64.zip -d /usr/local/bin \
	&& rm consul-template_${VERSION}_linux_amd64.zip \

	# dumb-init
	&& VERSION=1.2.0 \
	&& wget -O /usr/local/bin/dumb-init https://github.com/Yelp/dumb-init/releases/download/v$VERSION/dumb-init_${VERSION}_amd64 \
	&& chmod +x /usr/local/bin/dumb-init \

	# ruby
	&& apk add --no-cache ruby ruby-bundler ruby-json

COPY consul-wait /usr/local/bin/

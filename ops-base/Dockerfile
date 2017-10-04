FROM docker:17.06

ENTRYPOINT []
CMD []

RUN set -eux \
	&& apk add --no-cache wget \

	# docker-compose
	&& VERSION=1.16.1 \
	&& wget -O /usr/local/bin/docker-compose https://github.com/docker/compose/releases/download/$VERSION/run.sh \
	&& chmod +x /usr/local/bin/docker-compose \
	# run.sh is a bash script
	&& apk add --no-cache bash \

	# consul
	&& VERSION=0.7.5 \
	&& wget https://releases.hashicorp.com/consul/$VERSION/consul_${VERSION}_linux_amd64.zip \
	&& unzip consul_${VERSION}_linux_amd64.zip -d /usr/local/bin \
	&& rm consul_${VERSION}_linux_amd64.zip \

	# consul-template
	&& VERSION=0.18.5 \
	&& wget https://releases.hashicorp.com/consul-template/$VERSION/consul-template_${VERSION}_linux_amd64.zip \
	&& unzip consul-template_${VERSION}_linux_amd64.zip -d /usr/local/bin \
	&& rm consul-template_${VERSION}_linux_amd64.zip \

	# awscli
	&& apk add --no-cache python3 \
	&& pip3 install awscli \

	# dumb-init
	&& VERSION=1.2.0 \
	&& wget -O /usr/local/bin/dumb-init https://github.com/Yelp/dumb-init/releases/download/v$VERSION/dumb-init_${VERSION}_amd64 \
	&& chmod +x /usr/local/bin/dumb-init

COPY consul-wait /usr/local/bin/

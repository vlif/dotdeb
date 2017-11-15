FROM debian:8

MAINTAINER Valeriy Dubrava <vd@ddgcorp.ru>

ADD https://www.dotdeb.org/dotdeb.gpg /tmp/dotdeb.gpg

ENV TZ=Etc/UTC

RUN echo "Install DotDeb" \
	&& echo "deb http://packages.dotdeb.org jessie all" > /etc/apt/sources.list.d/dotdeb.list \
	&& echo "deb-src http://packages.dotdeb.org jessie all" >> /etc/apt/sources.list.d/dotdeb.list \
	&& apt-key add /tmp/dotdeb.gpg \
	&& rm /tmp/dotdeb.gpg \
	&& apt-get update && apt-get -y upgrade \
	&& echo "Common" \
	&& apt-get -y install apt-utils curl git \
	&& echo "Install PHP" \
	&& apt-get -y install php7.0 php7.0-cli php7.0-fpm php7.0-readline php7.0-redis php7.0-curl php7.0-gd php7.0-imagick php7.0-intl php7.0-mcrypt php7.0-memcache php7.0-mysql php7.0-pgsql php7.0-memcached \
	&& echo "Configure PHP" \
	&& echo "date.timezone=${TZ}" >> /etc/php/7.0/cli/php.ini && echo "date.timezone=${TZ}" >> /etc/php/7.0/fpm/php.ini \
	&& echo "Composer" \
	&& curl -sS https://getcomposer.org/installer | php && mv composer.phar /usr/bin/composer \
	&& echo "Cleanup" \
	&& apt-get purge -y --auto-remove -o APT::AutoRemove::RecommendsImportant=false -o APT::AutoRemove::SuggestsImportant=false

CMD ["/usr/bin/php"]

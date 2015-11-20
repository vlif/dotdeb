FROM debian:8

MAINTAINER Valeriy Dubrava <vd@ddgcorp.ru>

ADD https://www.dotdeb.org/dotdeb.gpg /tmp/dotdeb.gpg

ARG TZ=Etc/UTC

RUN echo "Install DotDeb" \
	&& echo "deb http://packages.dotdeb.org jessie all" > /etc/apt/sources.list.d/dotdeb.list \
	&& echo "deb-src http://packages.dotdeb.org jessie all" >> /etc/apt/sources.list.d/dotdeb.list \
	&& apt-key add /tmp/dotdeb.gpg \
	&& rm /tmp/dotdeb.gpg \
	&& apt-get update && apt-get -y upgrade \
	&& echo "Common" \
	&& apt-get -y install apt-utils curl git \
	&& echo "Install PHP" \
	&& apt-get -y install php5 php5-cli php5-fpm php5-readline php5-redis php5-curl php5-gd php5-imagick php5-intl php5-mcrypt php5-memcache php5-mysql php5-pgsql php5-memcached \
	&& echo "Configure PHP" \
	&& echo "date.timezone=${TZ}" >> /etc/php5/cli/php.ini && echo "date.timezone=${TZ}" >> /etc/php5/fpm/php.ini \
	&& echo "Composer" \
	&& curl -sS https://getcomposer.org/installer | php && mv composer.phar /usr/local/bin/composer \
	&& echo "Cleanup" \
	&& apt-get -y clean

CMD ["/bin/bash"]

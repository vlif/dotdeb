FROM ddgcorp/dotdeb-php:5.6

MAINTAINER Valeriy Dubrava <vd@ddgcorp.ru>

RUN echo "Install Apache" \
	&& apt-get update && apt-get -y upgrade \
	&& apt-get -y install apache2 libapache2-mod-php5 \
	&& echo "Configure PHP" \
	&& echo "date.timezone=${TZ}" >> /etc/php5/apache2/php.ini \ 
	&& echo "Cleanup" \
	&& apt-get purge -y --auto-remove -o APT::AutoRemove::RecommendsImportant=false -o APT::AutoRemove::SuggestsImportant=false

RUN mv /etc/apache2/apache2.conf /etc/apache2/apache2.conf.dist \
	&& mv /etc/apache2/envvars /etc/apache2/envvars.dist \
	&& mv /etc/apache2/sites-available/000-default.conf /etc/apache2/sites-available/000-default.conf.dist \
	&& rm /etc/apache2/conf-enabled/* /etc/apache2/sites-enabled/*

COPY apache2.conf /etc/apache2/apache2.conf
COPY envvars /etc/apache2/envvars
COPY 000-default.conf /etc/apache2/sites-available/000-default.conf
RUN ln -s /etc/apache2/sites-available/000-default.conf /etc/apache2/sites-enabled/000-default.conf
# enable rewrite module by default
RUN ln -s /etc/apache2/mods-available/rewrite.load /etc/apache2/mods-enabled/rewrite.load

COPY apache2-foreground /usr/local/bin/

EXPOSE 80
CMD ["apache2-foreground"]

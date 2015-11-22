FROM valerydubrava/dotdeb:php-5.6

MAINTAINER Valeriy Dubrava <vd@ddgcorp.ru>

RUN echo "Install Apache" \
	&& apt-get update && apt-get -y upgrade \
	&& apt-get -y install apache2 libapache2-mod-php5 \
	&& echo "Configure PHP" \
	&& echo "date.timezone=${TZ}" >> /etc/php5/apache2/php.ini \ 
	&& echo "Cleanup" \
	&& apt-get -y clean

#RUN mv /etc/apache2/apache2.conf /etc/apache2/apache2.conf.dist && rm /etc/apache2/conf-enabled/* /etc/apache2/sites-enabled/*

#COPY apache2.conf /etc/apache2/apache2.conf
COPY apache2-foreground /usr/local/bin/

EXPOSE 80
CMD ["apache2-foreground"]

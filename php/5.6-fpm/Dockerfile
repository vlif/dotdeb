FROM ddgcorp/dotdeb-php:5.6

RUN cp /etc/php5/fpm/php-fpm.conf /etc/php5/fpm/php-fpm.conf.dist
COPY php-fpm.conf /etc/php5/fpm/php-fpm.conf

EXPOSE 9000
CMD ["php5-fpm"]

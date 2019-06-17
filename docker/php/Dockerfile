From php:7.3-fpm

ENV MEMCACHED_USER=nobody

RUN apt-get update && apt-get install -y memcached libz-dev libmemcached-dev libmagickwand-dev \
    && pecl install imagick \
    && docker-php-ext-enable imagick

COPY entrypoint.sh /sbin/entrypoint.sh
RUN chmod 755 /sbin/entrypoint.sh
COPY info.php /var/www/html/info.php

EXPOSE 9000 11211
ENTRYPOINT ["/sbin/entrypoint.sh"]
CMD ["/usr/local/sbin/php-fpm"]

FROM php:7.1-fpm
MAINTAINER hundredlee <hundred9411@gmail.com>

WORKDIR /

ENV PHPREDIS_VERSION 3.1.2
RUN curl -L -o /tmp/redis.tar.gz https://github.com/phpredis/phpredis/archive/$PHPREDIS_VERSION.tar.gz \
 && tar xfz /tmp/redis.tar.gz \
 && rm -r /tmp/redis.tar.gz \
 && mkdir -p /usr/src/php/ext/redis \
 && mv phpredis-$PHPREDIS_VERSION/* /usr/src/php/ext/redis


# ADD source /source
# RUN chmod +x source
# RUN ./source

RUN apt-get update && apt-get install -y redis-server libpng12-dev libjpeg-dev bash \
  && docker-php-ext-configure gd --with-png-dir=/usr --with-jpeg-dir=/usr \
  && docker-php-ext-install gd mysqli pdo_mysql zip opcache redis


COPY ./config/php.ini /usr/local/etc/php/conf.d/
COPY ./config/opcache.ini /usr/local/etc/php/conf.d/

COPY ./config/redis.conf /etc/redis/redis.conf

# CMD ["redis-server","/etc/redis/redis.conf"]



FROM php:5.6-apache
RUN apt-get update \
    && apt-get install -y zip git libicu-dev libmcrypt-dev zlib1g-dev wget apt-transport-https \
    && docker-php-ext-install bcmath intl pdo_mysql pcntl mcrypt zip

RUN apt-get install -y libmagickwand-dev --no-install-recommends \
    && pecl install imagick \
    && docker-php-ext-enable imagick

RUN apt-get install -y libmemcached-dev \
    && pecl install memcache \
    && pecl install memcached-2.2.0 \
    && docker-php-ext-enable memcache memcached

RUN apt-get install -y libssl-dev \
    && pecl install mongo \
    && docker-php-ext-enable mongo

RUN docker-php-ext-install soap

COPY php.ini /usr/local/etc/php/

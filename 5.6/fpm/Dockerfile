FROM php:5.6-fpm

# httpredir.debian.org/debian fails too often, so replace it with a fixed mirror
RUN sed -i s#http://httpredir.debian.org#ftp://ftp.nl.debian.org#g /etc/apt/sources.list

RUN apt-get update \
    && apt-get install -y zip git libicu-dev wget apt-transport-https \
    && docker-php-ext-install bcmath intl pdo_mysql pcntl

RUN apt-get update \
    && apt-get install -y libmagickwand-dev --no-install-recommends \
    && pecl install imagick \
    && docker-php-ext-enable imagick

RUN apt-get install -y libssl-dev \
    && pecl install mongo \
    && docker-php-ext-enable mongo

RUN rm -rf /var/lib/apt/lists/*

COPY php.ini /usr/local/etc/php/

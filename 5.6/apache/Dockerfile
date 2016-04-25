FROM php:5.6-apache
RUN apt-get update \
    && apt-get install -y zip git libicu-dev libmcrypt-dev zlib1g-dev wget apt-transport-https \
    && docker-php-ext-install bcmath intl pdo_mysql pcntl mcrypt zip

RUN apt-get install -y libmagickwand-dev --no-install-recommends \
    && pecl install imagick \
    && docker-php-ext-enable imagick

RUN pecl install memcache \
    && docker-php-ext-enable memcache

RUN apt-get install -y libssl-dev \
    && pecl install mongo \
    && docker-php-ext-enable mongo

RUN docker-php-ext-install soap

COPY php.ini /usr/local/etc/php/

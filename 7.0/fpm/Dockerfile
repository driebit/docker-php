FROM php:7.0-fpm
RUN apt-get update \
    && apt-get install -y zip git libicu-dev wget \
    && docker-php-ext-install bcmath intl pdo_mysql pcntl

RUN git clone -b php7 https://github.com/phpredis/phpredis.git /usr/src/php/ext/redis \
    && docker-php-ext-install redis

RUN apt-get install -y libmagickwand-dev --no-install-recommends \
    && pecl install imagick \
    && docker-php-ext-enable imagick

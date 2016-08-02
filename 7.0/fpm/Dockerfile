FROM php:7.0-fpm

RUN apt-get update \
    && apt-get install -y zip git libicu-dev wget apt-transport-https \
    && docker-php-ext-install bcmath intl pdo_mysql pcntl

RUN pecl install redis \
    && docker-php-ext-enable redis

RUN apt-get update \
    && apt-get install -y libmagickwand-dev --no-install-recommends \
    && pecl install imagick \
    && docker-php-ext-enable imagick

RUN rm -rf /var/lib/apt/lists/*

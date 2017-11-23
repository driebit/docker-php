FROM php:5.6-fpm-alpine

ARG PHP_MODS="bcmath intl mbstring opcache pdo_mysql pcntl zip"
ARG PHP_MODS_DEPS="icu-dev zlib-dev"
ARG PHP_RUNTIME_DEPS="icu"

RUN apk add --no-cache --virtual .php-mods-dev $PHP_MODS_DEPS \
    && docker-php-ext-install $PHP_MODS \
    && apk del .php-mods-dev \
    && apk add --no-cache --virtual .php-mods-runtime $PHP_RUNTIME_DEPS

# Use gmagick instead of imagick because of segmentation fault on Alpine
RUN apk add --no-cache --virtual .phpize-deps $PHPIZE_DEPS libtool \
    && apk add --no-cache --repository http://dl-3.alpinelinux.org/alpine/v3.6/main/ jasper-dev \
    && apk add --no-cache --repository http://dl-3.alpinelinux.org/alpine/v3.6/community/ graphicsmagick-dev \
    && pecl install gmagick-1.1.7RC3 \
    && docker-php-ext-enable gmagick \
    && apk del .phpize-deps

COPY php.ini /usr/local/etc/php/

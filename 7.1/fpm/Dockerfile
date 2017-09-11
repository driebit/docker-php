FROM php:7.1-fpm-alpine

ARG MEMCACHED_DEPS="zlib-dev libmemcached-dev cyrus-sasl-dev"
ARG MONGODB_DEPS="openssl-dev"
ARG PECL_MODULES="memcached mongodb redis"

# PECL modules
RUN apk add --no-cache --virtual .phpize-deps $PHPIZE_DEPS \
    && apk add --no-cache --virtual .memcached-deps $MEMCACHED_DEPS \
    && apk add --no-cache --virtual .mongodb-deps $MONGODB_DEPS \
        && pecl install $PECL_MODULES \
    && docker-php-ext-enable $PECL_MODULES \
    && apk del .phpize-deps .memcached-deps .mongodb-deps \
    && apk add --no-cache libmemcached openssl

# Use gmagick instead of imagick because of segmentation fault on Alpine
RUN apk add --no-cache --virtual .phpize-deps $PHPIZE_DEPS libtool \
    && apk add --no-cache --repository http://dl-3.alpinelinux.org/alpine/v3.6/main/ jasper-dev \
    && apk add --no-cache --repository http://dl-3.alpinelinux.org/alpine/v3.6/community/ graphicsmagick-dev \
    && pecl install gmagick-beta  \
    && docker-php-ext-enable gmagick \
    && apk del .phpize-deps

# Built-in modules
RUN apk add --no-cache --virtual .phpize-deps $PHPIZE_DEPS icu-dev libxml2-dev \
    && docker-php-ext-install bcmath intl mbstring opcache pdo_mysql pcntl soap \
    && apk del .phpize-deps \
    && apk add --no-cache icu

FROM php:7.3-fpm-alpine

ARG MEMCACHED_DEPS="zlib-dev libmemcached-dev cyrus-sasl-dev"
ARG MONGODB_DEPS="openssl-dev bash"
ARG PECL_MODULES="memcached mongodb redis"

# PECL modules
RUN apk add --no-cache --virtual .phpize-deps $PHPIZE_DEPS \
    && apk add --no-cache --virtual .memcached-deps $MEMCACHED_DEPS \
    && apk add --no-cache --virtual .mongodb-deps $MONGODB_DEPS \
    && pecl install $PECL_MODULES \
    && docker-php-ext-enable $PECL_MODULES \
    && apk del .phpize-deps .memcached-deps .mongodb-deps \
    && apk add --no-cache libmemcached openssl

# Built-in modules
RUN apk add --no-cache --virtual .build-deps $PHPIZE_DEPS icu-dev libxml2-dev libzip-dev \
    && docker-php-ext-install bcmath intl opcache pdo_mysql pcntl soap zip \
    && apk del .build-deps \
    && apk add --no-cache icu libzip

# grep to fix '/bin/grep: unrecognized option: extended-regexp' during cache:clear
RUN apk add --no-cache acl grep

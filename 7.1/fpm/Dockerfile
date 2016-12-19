FROM php:7.1-fpm-alpine

RUN apk add --no-cache --virtual build-deps $PHPIZE_DEPS libtool \
    && apk add --no-cache icu-dev wget \

    # Use gmagick instead of imagick because of segmentation fault on Alpine
    && apk add --no-cache --repository http://dl-3.alpinelinux.org/alpine/edge/community/ graphicsmagick-dev \
    && pecl install gmagick-beta redis \
    && docker-php-ext-enable gmagick redis \
    && apk del build-deps

RUN docker-php-ext-install bcmath intl opcache pdo_mysql pcntl

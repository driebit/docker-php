FROM driebit/php:5.6-fpm

ENV COMPOSER_ALLOW_SUPERUSER 1
ENV COMPOSER_MEMORY_LIMIT -1

RUN apk add --no-cache --virtual build-deps $PHPIZE_DEPS libtool \
    && pecl install xdebug-2.5.5 \
    && docker-php-ext-enable xdebug \
    && apk del build-deps

COPY --from=composer:1.9.1 /usr/bin/composer /usr/bin/composer

COPY php.ini /usr/local/etc/php/

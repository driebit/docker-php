FROM driebit/php:5.6-fpm

ENV COMPOSER_ALLOW_SUPERUSER 1

RUN apk add --no-cache --virtual build-deps $PHPIZE_DEPS libtool \
    && pecl install xdebug \
    && docker-php-ext-enable xdebug \
    && apk del build-deps

RUN curl -sS https://getcomposer.org/installer | php -- --install-dir=/usr/bin/ --filename=composer

COPY php.ini /usr/local/etc/php/

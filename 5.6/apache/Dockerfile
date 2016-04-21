FROM php:5.6-apache
RUN apt-get update \
    && apt-get install -y zip git libicu-dev wget apt-transport-https \
    && docker-php-ext-install bcmath intl pdo_mysql pcntl

RUN apt-get install -y libmagickwand-dev --no-install-recommends \
    && pecl install imagick \
    && docker-php-ext-enable imagick

RUN pecl install mongo \
    && docker-php-ext-enable mongo

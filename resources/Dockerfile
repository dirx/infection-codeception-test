FROM php:7.3-cli-alpine

RUN apk update; \
    apk add --no-cache g++ make autoconf git zip unzip libzip-dev;\
    pecl install xdebug; \
    docker-php-ext-enable xdebug; \
    docker-php-ext-install -j$(nproc) zip; \
    curl -sS https://getcomposer.org/installer | php -- --install-dir=/usr/local/bin --filename=composer; \
    apk del g++ make autoconf;

ENTRYPOINT []

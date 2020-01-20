FROM composer:latest AS composer
FROM php:7.4-fpm

COPY --from=composer /usr/bin/composer /usr/bin/composer
WORKDIR /app

RUN apt-get update
RUN apt-get install -y gnupg2 curl

ENV PACKAGES="libpq-dev git libzip-dev libsodium-dev libpng-dev zip unzip"
ENV PHP_EXTENTIONS="pdo pdo_pgsql zip sodium"

RUN apt-get update
RUN apt-get install -y --no-install-recommends ${PACKAGES}
RUN docker-php-ext-install ${PHP_EXTENTIONS}

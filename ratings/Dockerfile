FROM php:7.4-apache

RUN apt-get update && apt-get install -y \
    git \
    unzip \
    zip \
    curl \
    libzip-dev \
    libcurl4-openssl-dev \
    && docker-php-ext-install \
        pdo_mysql \
        curl \
        zip \
        opcache

COPY status.conf /etc/apache2/mods-available/status.conf
RUN a2enmod rewrite status

WORKDIR /var/www/html

COPY html/ /var/www/html

COPY --from=composer:2 /usr/bin/composer /usr/bin/composer

RUN COMPOSER_ALLOW_SUPERUSER=1 composer install --no-interaction --prefer-dist

RUN rm -rf /var/www/var/*
RUN chown -R www-data:www-data /var/www
RUN chmod -R 777 /var/www

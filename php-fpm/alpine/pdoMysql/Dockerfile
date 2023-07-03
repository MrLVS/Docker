FROM php:8.1-fpm-alpine3.18
# Installing the PHP extension - pdo_mysql
RUN docker-php-ext-install -j$(nproc) pdo_mysql

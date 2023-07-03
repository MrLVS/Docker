FROM php:8.1-fpm-alpine3.18
# Installing the PHP extension - bz2
RUN set -eux; \
  apk add --no-cache bzip2-dev; \
  \
  docker-php-ext-install -j$(nproc) bz2

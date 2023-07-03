FROM php:8.1-fpm-alpine3.18
# Installing the PHP extension - zip
ARG PHPEXT_ZIP_VERSION=1.22.1
RUN set -eux; \
  persistentDeps="libzip"; \
  tmpDeps="libzip-dev"; \
  \
  apk add --no-cache ${persistentDeps}; \
  apk add --no-cache --virtual .zip-tmp-deps ${tmpDeps}; \
  \
  pecl bundle -d /usr/src/php/ext zip-${PHPEXT_ZIP_VERSION}; \
  docker-php-ext-install -j$(nproc) zip; \
  \
  apk del --no-cache .zip-tmp-deps; \
  docker-php-source delete; \
  rm -rf /tmp/* /var/tmp/*

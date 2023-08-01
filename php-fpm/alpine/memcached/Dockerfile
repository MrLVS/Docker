FROM php:8.1-fpm-alpine3.18
# Installing the PHP extension - memcached
ARG PHPEXT_MEMCACHED_VERSION=3.2.0
RUN set -eux; \
  persistentDeps=" \
    libmemcached \
    libzip \
  "; \
  tmpDeps=" \
    libmemcached-dev \
    libzip-dev \
  "; \
  apk add --no-cache ${persistentDeps}; \
  apk add --no-cache --virtual .tmp-deps ${tmpDeps}; \
  \
  pecl bundle -d /usr/src/php/ext memcached-${PHPEXT_MEMCACHED_VERSION}; \
  docker-php-ext-install -j$(nproc) memcached; \
  \
  apk del --no-cache --no-network .tmp-deps; \
  docker-php-source delete; \
  rm -rf /tmp/* /var/tmp/*

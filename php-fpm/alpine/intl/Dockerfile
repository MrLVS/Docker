FROM php:8.1-fpm-alpine3.18
# Installing the PHP extension - intl
RUN set -eux; \
  persistentDeps="icu"; \
  tmpDeps="icu-dev"; \
  apk add --no-cache ${persistentDeps}; \
  apk add --no-cache --virtual .intl-tmpDeps ${tmpDeps}; \
  \
  docker-php-ext-install -j$(nproc) intl; \
  \
  apk del --no-cache --no-network .intl-tmpDeps

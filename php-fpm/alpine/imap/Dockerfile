FROM php:8.1-fpm-alpine3.18
# Installing the PHP extension - imap
RUN set -eux; \
  tmpDeps=" \
    imap-dev \
    openssl-dev \
  "; \
  apk add --no-cache c-client; \
  apk add --no-cache --virtual .imap-tmpDeps ${tmpDeps}; \
  \
  docker-php-ext-install -j$(nproc) imap; \
  \
  apk del --no-cache .imap-tmpDeps

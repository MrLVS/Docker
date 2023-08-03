FROM php:8.1-fpm-alpine3.18
# Installing the PHP extension - gmp
RUN set -eux; \
  tmpDeps="gmp-dev"; \
  \
  apk add --no-cache gmp ; \
  apk add --no-cache --virtual .gmp-tmpDeps ${tmpDeps}; \
  \
  docker-php-ext-install -j$(nproc) gmp; \
  \
  apk del --no-cache .gmp-tmpDeps

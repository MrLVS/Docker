FROM php:8.1-fpm-alpine3.18
# Installing the PHP extension - pdo_pgsql
RUN set -eux; \
  persistentDeps="libpq"; \
  tmpDeps="postgresql-dev"; \
  \
  apk add --no-cache ${persistentDeps}; \
  apk add --no-cache --virtual .pdo_pgsql-tmpDeps ${tmpDeps}; \
  \
  docker-php-ext-install -j$(nproc) pdo_pgsql; \
  \
  apk del --no-cache --no-network .pdo_pgsql-tmpDeps

FROM php:8.1-fpm-alpine3.18
# Installing the PHP extension - gd
RUN set -eux; \
  persistentDeps=" \
    freetype \
    libjpeg-turbo \
    libpng \
    libwebp \
    libxpm \
  "; \
  tmpDeps=" \
    freetype-dev \
    libjpeg-turbo-dev \
    libpng-dev \
    libwebp-dev \
    libxpm-dev \
  "; \
  apk add --no-cache --virtual .gd-persistent-deps ${persistentDeps}; \
  apk add --no-cache --virtual .gd-tmpDeps ${tmpDeps}; \
  \
  docker-php-ext-configure gd \
    --with-freetype \
    --with-jpeg \
  ; \
  docker-php-ext-install -j$(nproc) gd; \
  \
  apk del --no-cache .gd-tmpDeps

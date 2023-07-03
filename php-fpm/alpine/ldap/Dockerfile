FROM php:8.1-fpm-alpine3.18
# Installing the PHP extension - ldap
RUN set -eux; \
  persistentDeps="libldap"; \
  tmpDeps="openldap-dev"; \
  apk add --no-cache ${persistentDeps}; \
  apk add --no-cache --virtual .ldap-tmpDeps ${tmpDeps}; \
  \
  docker-php-ext-install -j$(nproc) ldap; \
  \
  apk del --no-cache --no-network .ldap-tmpDeps

FROM php:8.1-fpm-alpine AS app_php
RUN echo 'app_php'

FROM app_php AS app_php_prod
RUN echo 'app_php_prod'
#define custom options for "prod"

FROM app_php AS app_php_ci
RUN echo 'app_php_ci'
#define custom options for "ci"

FROM app_php AS app_php_dev_performance
RUN echo 'app_php_dev_performance'
#define custom options for "dev performance"

FROM app_php AS app_php_dev
RUN echo 'app_php_dev'

#add package for installing php extensions
COPY --from=mlocati/php-extension-installer  /usr/bin/install-php-extensions /usr/local/bin/

#install xdebug
RUN set -eux; install-php-extensions xdebug;

#add some xdebug ini settings
COPY xdebug.ini /tmp/xdebug.ini
RUN cp /tmp/xdebug.ini /usr/local/etc/php/conf.d/xdebug.ini;

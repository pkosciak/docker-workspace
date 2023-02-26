FROM php:8.0.15-fpm-alpine

ADD https://github.com/mlocati/docker-php-extension-installer/releases/latest/download/install-php-extensions /usr/local/bin/

RUN chmod +x /usr/local/bin/install-php-extensions && sync \
    && install-php-extensions pdo_mysql \
        fileinfo \
        mysqli

COPY --from=composer /usr/bin/composer /usr/bin/composer

RUN curl -O https://raw.githubusercontent.com/wp-cli/builds/gh-pages/phar/wp-cli.phar && \
    chmod +x wp-cli.phar && \
    mv wp-cli.phar /usr/local/bin/wp-cli.phar && \
    echo '#!/bin/sh' >> /usr/local/bin/wp && \
    echo 'wp-cli.phar "$@" --allow-root' >> /usr/local/bin/wp && \
    chmod +x /usr/local/bin/wp

RUN apk add --update linux-headers

RUN apk --no-cache add shadow && usermod -u 1000 www-data

COPY .docker/xdebug/xdebug.ini "${PHP_INI_DIR}/conf.d"

RUN chown -R www-data:www-data /var/www/html
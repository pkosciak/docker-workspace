FROM php:8.0.15-fpm-alpine

ADD https://github.com/mlocati/docker-php-extension-installer/releases/latest/download/install-php-extensions /usr/local/bin/

RUN chmod +x /usr/local/bin/install-php-extensions && sync \
    && install-php-extensions pdo_mysql \
        fileinfo \
        mysqli

COPY --from=composer /usr/bin/composer /usr/bin/composer

RUN apk --no-cache add shadow && usermod -u 1000 www-data

RUN chown -R www-data:www-data /var/www/html
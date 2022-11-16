ARG phpvers

FROM php:${PHPVERS}-fpm-alpine

RUN apk add apache2-proxy
RUN echo "ServerName laravel-app.local" >> /etc/apache2/httpd.conf
RUN mkdir /var/www/
ENV APACHE_DOCUMENT_ROOT=
RUN sed -ri -e 's!/var/www/localhost!/var/www/!g' /etc/apache2/httpd.conf

RUN mv "$PHP_INI_DIR/php.ini-development" "$PHP_INI_DIR/php.ini"

RUN docker-php-ext-install pdo pdo_mysql sockets

COPY --from=composer:latest /usr/bin/composer /usr/bin/composer

ARG uid
RUN adduser -u $uid -D elitery-test
RUN addgroup elitery-test www-data
RUN addgroup elitery-test root

RUN mkdir -p /home/eliterytest/.composer && \
    chown -R eliterytest:eliterytest /home/eliterytest
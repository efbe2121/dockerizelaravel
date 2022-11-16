FROM php:7.4.33-fpm-alpine

RUN apk add --no-cache apache2 php-apache2 zlib-dev icu-dev libpng-dev icu-libs icu-data-full

ENV APACHE_DOCUMENT_ROOT /var/www/app/public
RUN mkdir /var/www/app

RUN docker-php-ext-install pdo pdo_mysql sockets gd intl mysqli

COPY --from=composer:latest /usr/bin/composer /usr/bin/composer

RUN chmod -R 755 /var/www/app
RUN chown -R www-data:www-data /var/www/app

# RUN adduser -u 1000 -D elitery-test
# RUN addgroup elitery-test elitery-test
# RUN addgroup elitery-test www-data
# RUN addgroup elitery-test root

# RUN mkdir -p /home/elitery-test/.composer && \
#     chown -R elitery-test:elitery-test /home/elitery-test
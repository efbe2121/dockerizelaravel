FROM php:7.4.33-fpm-alpine

COPY composer.lock /var/www/html/
COPY composer.json /var/www/html/

WORKDIR /var/www/html

RUN apk --update --no-cache add \
    build-base shadow vim curl \
    php-fpm \
    php-common \
    php-pdo \
    php-pdo_mysql \
    php-mysqli \
    php-mbstring \
    php-xml \
    php-openssl \
    php-json \
    php-phar \
    php-zip \
    php-gd \
    php-dom \
    php-session \
    php-zlib

RUN docker-php-ext-install pdo pdo_mysql && docker-php-ext-enable pdo_mysql
RUN curl -sS https://getcomposer.org/installer | php -- --install-dir=/usr/local/bin --filename=composer
RUN rm -rf /var/cache/apk/*
RUN usermod -u 1000 www-data
RUN chown www-data:www-data /var/www/html

USER www-data
EXPOSE 9000

CMD ["php-fpm"]
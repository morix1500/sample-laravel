FROM php:7.2-fpm-alpine

RUN apk --update add vim freetype-dev libjpeg-turbo-dev libpng-dev shadow && \
    docker-php-ext-install pdo_mysql mbstring gd zip

ARG PUID=1000
ENV PUID ${PUID}
ARG PGID=1000
ENV PGID ${PGID}

RUN groupadd -g ${PGID} laravel && \
    useradd -u ${PUID} -g laravel -m laravel && \
    usermod -p "*" laravel -s /bin/sh


# install composer
RUN curl -sS https://getcomposer.org/installer | php -- --install-dir=/usr/local/bin --filename=composer

USER laravel
RUN composer global require "laravel/installer"
ENV PATH $PATH:/home/laravel/.composer/vendor/bin

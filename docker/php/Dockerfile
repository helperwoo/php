FROM php:8.0.2-fpm

RUN apt-get update
RUN apt-get install -y curl

#install some base extensions
RUN apt-get install -y \
        zlib1g-dev \
        zip \
        libpng-dev \
        exiftool \
        libfreetype6-dev \
        libjpeg62-turbo-dev \
        libmcrypt-dev \
        libicu-dev \
        libpq-dev \
        libxpm-dev \
        libvpx-dev \
        libzip-dev \
        mariadb-client \
        libxml2-dev \
        vim

RUN docker-php-ext-configure gd --enable-gd --with-freetype --with-jpeg
RUN docker-php-ext-install mysqli pdo_mysql exif gd bcmath zip

# node install
RUN curl -sL https://deb.nodesource.com/setup_12.x
RUN apt-get install -y nodejs

# Composer install
RUN curl -sS https://getcomposer.org/installer | php
RUN mv composer.phar /usr/local/bin/composer

WORKDIR /home/app

CMD ["php-fpm"]
FROM php:8.3-fpm

# Install system dependencies
RUN apt-get update && apt-get install -y \
    curl git unzip zip \
    libpng-dev libjpeg62-turbo-dev libfreetype6-dev libwebp-dev \
    libicu-dev libgmp-dev libpq-dev libxpm-dev libvpx-dev libzip-dev mariadb-client \
    libxml2-dev libonig-dev libmagickwand-dev \
    build-essential autoconf pkg-config \
    vim nano htop procps net-tools iputils-ping \
    && rm -rf /var/lib/apt/lists/*

# Install PHP extensions via PECL
RUN pecl install redis xdebug imagick
RUN docker-php-ext-enable redis xdebug imagick

# Configure and install PHP core extensions
RUN docker-php-ext-configure gd --enable-gd --with-freetype --with-jpeg --with-webp
RUN docker-php-ext-install bcmath exif mysqli pdo_mysql gd zip pcntl sockets gmp intl mbstring xml soap opcache

# Install Composer
RUN curl -sS https://getcomposer.org/installer | php
RUN mv composer.phar /usr/local/bin/composer

WORKDIR /home/app

CMD ["php-fpm"]
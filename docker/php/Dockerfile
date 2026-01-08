# PHP 8.3 CLI + FPM + kerakli ext lar
FROM php:8.3-fpm

# Kerakli paketlar o'rnatish
RUN apt-get update && apt-get install -y \
    git \
    unzip \
    curl \
    libzip-dev \
    libpng-dev \
    libjpeg-dev \
    libfreetype6-dev \
    libonig-dev \
    libxml2-dev \
    libicu-dev \
    libcurl4-openssl-dev \
    pkg-config \
    && docker-php-ext-install pdo_mysql mbstring zip exif pcntl gd intl soap curl

# Composer o'rnatish
COPY --from=composer:2 /usr/bin/composer /usr/bin/composer

WORKDIR /var/www/html

# Laravel loyihasini ishga tushirish uchun
CMD ["php-fpm"]

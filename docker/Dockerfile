FROM php:7.4-apache

# Install dependencies
RUN apt-get update && \
    apt-get install -y \
        libpng-dev \
        libzip-dev \
        zip \
        unzip

# Configure PHP
RUN docker-php-ext-install pdo pdo_mysql gd zip
RUN a2enmod rewrite

# Install Composer
COPY --from=composer:latest /usr/bin/composer /usr/bin/composer

# Copy app
COPY src /var/www/html
WORKDIR /var/www/html

# Install dependencies
RUN composer install --no-dev --optimize-autoloader
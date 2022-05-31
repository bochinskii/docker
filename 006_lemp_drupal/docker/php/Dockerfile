FROM php:8.0-fpm

#
# Install libraries for extantions
#
RUN apt-get update && apt-get install -y \
                      libxml2-dev \
                      libfreetype6-dev \
		                  libjpeg62-turbo-dev \
		                  libpng-dev \
                      libedit-dev \
                      libcurl4-openssl-dev \
                      libonig-dev \
                      libgmp-dev \
                      libzip-dev \
                      libtidy-dev

#
# Install extentions
#
RUN docker-php-ext-install \
    opcache \
    xml \
    gd \
    curl \
    mbstring \
    gmp \
    intl \
    zip \
    pdo \
    pdo_mysql \
    tidy \
    soap \
    bcmath

#
# Copy configs
#

# $PHP_INI_DIR = /usr/local/etc/php
COPY ./php.ini $PHP_INI_DIR/php.ini

# TEST
#
#
#RUN useradd -s /usr/sbin/nologin -M nginx

#RUN sed -i "s/^user = .*/user = nginx/g" /usr/local/etc/php-fpm.d/www.conf \
#    && sed -i "s/^group = .*/group = nginx/g" /usr/local/etc/php-fpm.d/www.conf \
#    && sed -i "s/^;listen.owner = .*/listen.owner = nginx/g" /usr/local/etc/php-fpm.d/www.conf \
#    && sed -i "s/^;listen.group = .*/listen.group = nginx/g" /usr/local/etc/php-fpm.d/www.conf \
#    && sed -i "s/^;listen.mode = .*/listen.mode = 0660/g" /usr/local/etc/php-fpm.d/www.conf

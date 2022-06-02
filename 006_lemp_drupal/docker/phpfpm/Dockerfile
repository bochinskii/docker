FROM drupal:9.3.13-php8.0-fpm-alpine3.15

#
# php.ini
#
RUN mv $PHP_INI_DIR/php.ini-production $PHP_INI_DIR/php.ini


RUN sed -i "s/^short_open_tag = .*/short_open_tag = On/g" $PHP_INI_DIR/php.ini \
    && sed -i "s/^memory_limit = .*/memory_limit = 256M/g" $PHP_INI_DIR/php.ini \
    && sed -i "s/^upload_max_filesize = .*/upload_max_filesize = 100M/g" $PHP_INI_DIR/php.ini \
    && sed -i "s/^post_max_size = .*/post_max_size = 100M/g" $PHP_INI_DIR/php.ini \
    && sed -i "s/^max_execution_time = .*/max_execution_time = 300/g" $PHP_INI_DIR/php.ini \
    && sed -i "s%^;date.timezone =%date.timezone = Europe/Moscow%g" $PHP_INI_DIR/php.ini

#
# Add libraries for extantions
#
RUN apk upgrade --update-cache --available && apk add libxml2-dev \
                                           curl-dev \
                                           oniguruma-dev \
                                           gmp-dev \
                                           icu-dev

#
# Add  extantions
#
RUN docker-php-ext-install xml \
                           curl \
                           mbstring \
                           gmp \
                           intl

#
# Custome Site
#
#COPY ./drupal.tar.bz /tmp/drupal.tar.bz

#RUN rm -fr /var/www/html/ && mkdir /var/www/html \
#    && tar -xvf /tmp/drupal.tar.bz -C /var/www/html --strip-components=1 \
#    && chown -R www-data: /var/www/html/modules \
#    && chown -R www-data: /var/www/html/sites \
#    && chown -R www-data: /var/www/html/themes

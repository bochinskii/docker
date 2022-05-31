FROM nginx:1.21

#
# Copy configs
#
COPY ./configs/conf.d/*.conf /etc/nginx/conf.d/

COPY ./configs/nginx.conf /etc/nginx/

#
# TLS
#
COPY ./configs/rocinante.crt /etc/nginx/tls/

COPY ./configs/rocinante.key /etc/nginx/tls/

RUN chmod 0400 /etc/nginx/tls/rocinante.key && openssl dhparam -out /etc/nginx/tls/dhparam.pem 2048

#
# Install Drupal 9
#
RUN mkdir -p /var/www/html && curl -Lo /tmp/drupal.tar.gz https://www.drupal.org/download-latest/tar.gz \
                           && tar -xzvf /tmp/drupal.tar.gz -C /var/www/html --strip-components=1 \
                           && chmod -R 755 /var/www/html/sites/default/ \
                           && cp /var/www/html/sites/default/default.settings.php /var/www/html/sites/default/settings.php \
                           && chmod 666 /var/www/html/sites/default/settings.php


EXPOSE 80 443

FROM nginx:1.22-alpine

#
# Copy configs
#
COPY ./configs/conf.d/*.conf /etc/nginx/conf.d/

COPY ./configs/nginx.conf /etc/nginx/

#
# TLS
#

RUN apk upgrade --update-cache --available && apk add openssl && rm -rf /var/cache/apk/*

RUN mkdir /etc/nginx/tls && openssl dhparam -out /etc/nginx/tls/dhparam.pem 2048 \
                         && openssl req -x509 -nodes -days 365 -newkey rsa:2048 \
                         -keyout /etc/nginx/tls/rocinante.key -out /etc/nginx/tls/rocinante.crt \
                         -subj "/C=RU/ST= /L=Donets/O= /OU= /CN=rocinante.in"


EXPOSE 80 443 8080 4343

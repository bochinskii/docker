FROM debian:latest

RUN apt-get update && apt-get install curl gnupg2 ca-certificates lsb-release debian-archive-keyring -y

RUN apt-get update; apt-get install nginx -y

VOLUME /var/www/html /etc/nginx

EXPOSE 80/tcp 443/tcp

STOPSIGNAL SIGQUIT

CMD ["nginx", "-g", "daemon off;"]

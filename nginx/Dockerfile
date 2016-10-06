FROM nginx:alpine

RUN rm -v /etc/nginx/conf.d/*
COPY config/portainer.conf /etc/nginx/conf.d/portainer.conf
COPY config/auth.htpasswd /etc/nginx/conf.d/auth.htpasswd

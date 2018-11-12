FROM nginx:stable-alpine

ARG REGISTRY_USER
ARG REGISTRY_PASSWORD
ARG DOMAIN

COPY /default.conf /etc/nginx/conf.d/default.conf

RUN echo "$REGISTRY_USER:{PLAIN}$REGISTRY_PASSWORD" >/etc/nginx/conf.d/registry.password && \
  sed -i "s/@DOMAIN@/${DOMAIN}/g" /etc/nginx/conf.d/default.conf && \
  mkdir /data

ADD ./homepage /data/homepage

# Inherit CMD from parent as we have no entrypoint

FROM php:7.4-cli-alpine

RUN apk add --no-cache \
    $PHPIZE_DEPS \
    openssl-dev;
RUN pecl install xdebug;
RUN docker-php-ext-enable xdebug;

COPY --from=composer:latest /usr/bin/composer /usr/bin/composer

ARG USER=docker
ARG UID=1000
ARG GID=1000
ARG PW=docker

RUN addgroup -S ${GID};
RUN adduser -S ${USER} -G ${UID};
RUN echo "${USER}:${PW}" | chpasswd;

USER ${UID}:${GID}

WORKDIR /app

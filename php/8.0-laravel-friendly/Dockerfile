FROM php:8.0-fpm-alpine

RUN apk add --update --no-cache $PHPIZE_DEPS \
    openssl-dev \
    imagemagick \
    imagemagick-dev \
    libpng \
    libpng-dev \
    zip \
    libzip-dev \
    unzip \
    libtool \
    make \
    pcre-dev \
    libpq-dev;

RUN pecl install xdebug \
    imagick;

RUN docker-php-ext-enable xdebug;
RUN docker-php-ext-enable imagick;
RUN docker-php-ext-install gd \
    zip \
    pdo \
    pdo_mysql \
    pdo_pgsql;

RUN apk del autoconf \
    g++ \
    libtool \
    make \
    pcre-dev \
    libpng-dev;

COPY --from=composer:latest /usr/bin/composer /usr/bin/composer

EXPOSE 9000

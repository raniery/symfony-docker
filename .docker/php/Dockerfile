FROM php:7.1.6-fpm

MAINTAINER Raniery Ribeiro <raniery.rrr@gmail.com>

RUN apt-get update \
	&& apt-get install -y \
	libpq-dev \
	libmcrypt-dev \
	libmagickwand-dev --no-install-recommends \
	zip \
	unzip \
	vim \
	wget \
	curl \
	git \
	mysql-client \
	moreutils \
	dnsutils \
	zlib1g-dev \
	libicu-dev \
	libmemcached-dev \
	g++ \
	&& rm -rf /var/lib/apt/lists/* \
	&& pecl install imagick \
    && docker-php-ext-enable imagick \
    && docker-php-ext-configure pgsql -with-pgsql=/usr/local/pgsql \
	&& docker-php-ext-configure intl \
    && docker-php-ext-install pdo pdo_pgsql pgsql mcrypt pdo_mysql opcache intl

# install xdebug
RUN pecl install xdebug
RUN docker-php-ext-enable xdebug \
    && echo "error_reporting = E_ALL" >> /usr/local/etc/php/conf.d/docker-php-ext-xdebug.ini \
    && echo "display_startup_errors = On" >> /usr/local/etc/php/conf.d/docker-php-ext-xdebug.ini \
    && echo "display_errors = On" >> /usr/local/etc/php/conf.d/docker-php-ext-xdebug.ini \
    && echo "xdebug.remote_enable = 1" >> /usr/local/etc/php/conf.d/docker-php-ext-xdebug.ini \
    && echo "xdebug.remote_connect_back = 1" >> /usr/local/etc/php/conf.d/docker-php-ext-xdebug.ini \
    && echo "xdebug.idekey = \"PHPSTORM\"" >> /usr/local/etc/php/conf.d/docker-php-ext-xdebug.ini \
    && echo "xdebug.remote_port = 9001" >> /usr/local/etc/php/conf.d/docker-php-ext-xdebug.ini

EXPOSE 9000
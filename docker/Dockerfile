FROM php:8.2-fpm AS php

RUN apt-get update && apt-get install -y \
		libfreetype6-dev \
		libjpeg62-turbo-dev \
		libpng-dev \
	&& docker-php-ext-configure gd --with-freetype --with-jpeg \
	&& docker-php-ext-install -j$(nproc) gd \
    && apt-get update && apt install -y libicu-dev libpq-dev libxml2-dev libzip-dev\
    && docker-php-ext-install intl pgsql pdo_pgsql pdo_mysql mysqli soap sockets bcmath zip

RUN apt-get install -y git
COPY --from=composer:2.5 /usr/bin/composer /usr/local/bin/composer
#COPY . /var/www/html
# Create the non-root runtime user.  It does not need a
# specific uid, shell, home directory, or other settings.

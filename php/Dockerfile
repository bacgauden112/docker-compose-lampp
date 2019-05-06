FROM php:7.1-apache
RUN apt-get update
RUN apt-get install -y libmcrypt-dev
RUN apt-get install -y \
		libfreetype6-dev \
		libjpeg62-turbo-dev \
		libpng-dev \
	&& docker-php-ext-install -j$(nproc) iconv \
	&& docker-php-ext-configure gd --with-freetype-dir=/usr/include/ --with-jpeg-dir=/usr/include/ \
	&& docker-php-ext-install -j$(nproc) gd
RUN docker-php-ext-install mcrypt
RUN mv "$PHP_INI_DIR/php.ini-production" "$PHP_INI_DIR/php.ini"
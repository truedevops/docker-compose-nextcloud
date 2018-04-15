FROM php:7.2-fpm

#MAINTAINER Mahmoud Zalt <mahmoud@zalt.me>
# Install "curl", "libmemcached-dev", "libpq-dev", "libjpeg-dev",
#         "libpng-dev", "libfreetype6-dev", "libssl-dev", "libmcrypt-dev",
RUN apt-get update \
  && apt-get install -y --no-install-recommends \
    curl \
    libmemcached-dev \
    libz-dev \
    libpq-dev \
    libjpeg-dev \
    libpng-dev \
    libfreetype6-dev \
    libssl-dev \
    libmcrypt-dev \
    libxml2-dev \
    libxslt1-dev \
    zlib1g-dev \
    libzip-dev \
    zip \
  && rm -rf /var/lib/apt/lists/*

RUN docker-php-ext-install pdo_mysql \
  && docker-php-ext-install pdo_pgsql \
  && docker-php-ext-configure gd \
    --enable-gd-native-ttf \
    --with-jpeg-dir=/usr/lib \
    --with-freetype-dir=/usr/include/freetype2 && \
     docker-php-ext-configure zip --with-libzip && \
#  && docker-php-ext-install zip
     pecl install memcached-3.0.3 && \
     pecl install apcu-5.1.5 && \
     pecl install redis && \
     docker-php-ext-enable memcached && \
     docker-php-ext-enable redis && \
     docker-php-ext-enable apcu && \
     docker-php-ext-install gd \
	exif \
	opcache \
	calendar \
	mysqli \
	pdo \
	bcmath \
  	gettext \
	pcntl \
	xsl \
        zip && \
     docker-php-source delete

RUN rm /usr/local/etc/php-fpm.d/www.conf.default \
    && rm /usr/local/etc/php-fpm.conf.default 

COPY ./conf/php.ini /usr/local/etc/php/conf.d/php.ini
COPY ./conf/www.conf /usr/local/etc/php-fpm.d/www.conf

EXPOSE 9000

CMD ["php-fpm"]

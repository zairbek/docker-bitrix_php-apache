FROM php:7.1-apache
RUN apt-get update && apt-get install -y \
	zip \
	unzip \
    curl \
    wget \
    git \
	nano \
    libfreetype6-dev \
    libjpeg62-turbo-dev \
    libmcrypt-dev \
    libpng-dev \
	libwebp-dev \
	libxpm-dev \
	zlib1g-dev \
	libzip-dev 

RUN docker-php-ext-install -j$(nproc) opcache iconv mbstring mysqli pdo_mysql zip \
    && docker-php-ext-configure gd --with-freetype-dir=/usr/include/ --with-jpeg-dir=/usr/include/ \
    && docker-php-ext-install -j$(nproc) gd \
    && docker-php-ext-configure gd --with-gd --with-webp-dir --with-jpeg-dir \
      --with-png-dir --with-zlib-dir --with-xpm-dir --with-freetype-dir \
    && docker-php-ext-configure zip --with-libzip

RUN mv "$PHP_INI_DIR/php.ini-production" "$PHP_INI_DIR/php.ini"


ARG USER_ID
ARG GROUP_ID

USER root

RUN if getent passwd www-data; then \
    userdel -f www-data && \
    if getent group www-data; then \
    groupdel www-data; \
    fi && \
    groupadd -g ${GROUP_ID} www-data && \
    useradd -l -u ${USER_ID} -g www-data  www-data; \
    fi
    
USER www-data

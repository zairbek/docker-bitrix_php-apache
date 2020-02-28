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

















# FROM ubuntu:latest
# RUN add-apt-repository ppa:ondrej/php \ 
#     && apt-get update && apt-get install -y \
#         php7.1 \
#         php7.1-fpm \
#         php7.1-opcache \
#         php7.1-zip \
#         php7.1-xmlrpc \
#         php7.1-xsl \
#         php7.1-mbstring \
#         php7.1-mcrypt \
#         php7.1-mysql \
#         php7.1-odbc \
#         php7.1-pgsql \
#         php7.1-pspell \
#         php7.1-readline \
#         php7.1-recode \
#         php7.1-snmp \
#         php7.1-soap \
#         php7.1-sqlite3 \
#         php7.1-sybase \
#         php7.1-tidy \
#         php7.1-xml \
#         php7.1-json \
#         php7.1-ldap \
#         php7.1-intl \
#         php7.1-interbase \
#         php7.1-imap \
#         php7.1-gmp \
#         php7.1-gd \
#         php7.1-enchant \
#         php7.1-dba \
#         php7.1-bz2 \
#         php7.1-bcmath \
#         php7.1-phpdbg \
#         php7.1-cgi \
#         php7.1-cli \
#         php7.1-curl


# FROM debian:9

# USER root

# # Get Debian up-to-date
# RUN apt-get update -qq \
#     && DEBIAN_FRONTEND=noninteractive apt-get install -y git \
#     mariadb-client wget curl \
#     ca-certificates lsb-release apt-transport-https gnupg bsdmainutils

# # Install 3rd party PHP 7.2 packages
# RUN echo "deb https://packages.sury.org/php/ $(lsb_release -sc) main" | tee -a /etc/apt/sources.list.d/php.list
# RUN curl -L https://packages.sury.org/php/apt.gpg | apt-key add -

# RUN  apt-get update -qq \
#     && DEBIAN_FRONTEND=noninteractive apt-get install -y php7.2 php7.2-common php7.2-cli php7.2-fpm \
#     php7.2-mysql  php7.2-curl php7.2-xml php7.2-mbstring \
#     php7.2-intl php7.2-redis php7.2-zip tidy \
#     php7.2-imagick

# # Make the default directory you
# WORKDIR /var/www

# # Run the process that this container will serve
# CMD ["/usr/sbin/php-fpm7.2", "--nodaemonize", "--fpm-config=/var/www/docker/php_fpm/config/fpm.conf", "-c", "/var/www/docker/php_fpm/config/php.ini"]

# #CMD tail -f README.md
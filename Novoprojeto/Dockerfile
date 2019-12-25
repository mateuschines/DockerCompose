FROM php:7.2.25-apache-stretch

MAINTAINER Mateus Rocha

RUN apt-get update && apt-get install -y \
    git \
    zlib1g-dev \
    unzip \
    unixodbc \
    unixodbc-dev \
    freetds-dev \
    freetds-bin \
    tdsodbc \
    libxml2-dev \
    libicu-dev \
    locales-all \
    task-brazilian-portuguese \
    ghostscript \
    libaio-dev \
    unixodbc \
    tdsodbc \
    libzip-dev \
    && docker-php-ext-install zip \
    && docker-php-ext-install sockets

# Set timezone
RUN rm /etc/localtime &&\
    ln -s /usr/share/zoneinfo/America/Sao_Paulo /etc/localtime &&\
    "date"

# install pecl
RUN curl -O http://pear.php.net/go-pear.phar \
    ; /usr/local/bin/php -d detect_unicode=0 go-pear.phar

# Driver Mysql Pdo
RUN docker-php-ext-install pdo pdo_mysql zip
RUN docker-php-ext-install mysqli

#Composer
RUN curl -sS https://getcomposer.org/installer | php -- --install-dir=/usr/local/bin --filename=composer

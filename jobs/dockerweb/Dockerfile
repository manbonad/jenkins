FROM php:7.4-apache
LABEL maintainer="Jaivic"

RUN a2enmod rewrite

# Actualizar la lista de paquetes e instalar las dependencias
RUN apt-get update && apt-get install -y \
    zlib1g-dev \
    libicu-dev \
    libxml2-dev \
    libpq-dev \
    libzip-dev \
    vim && \
    docker-php-ext-configure pgsql --with-pgsql=/usr/local/pgsql && \
    docker-php-ext-install pdo pdo_mysql pdo_pgsql zip intl xmlrpc soap opcache && \
    docker-php-ext-configure pdo_mysql --with-pdo-mysql=mysqlnd && \
    apt-get clean && rm -rf /var/lib/apt/lists/*

COPY . /var/www/html/
WORKDIR /var/www/html/





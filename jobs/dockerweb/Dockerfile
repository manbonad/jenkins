FROM php:7.1.17-apache
LABEL maintainer="Jaivic"

# Habilitar el módulo de reescritura de Apache
RUN a2enmod rewrite

# Actualizar la lista de paquetes e instalar las dependencias
RUN apt-get update && apt-get install -y \
    zlib1g-dev \
    libicu-dev \
    libxml2-dev \
    libpq-dev \
    vim && \
    docker-php-ext-configure pgsql --with-pgsql=/usr/local/pgsql && \
    docker-php-ext-install pdo pdo_mysql pdo_pgsql zip intl xmlrpc soap opcache && \
    docker-php-ext-configure pdo_mysql --with-pdo-mysql=mysqlnd && \
    apt-get clean && rm -rf /var/lib/apt/lists/*

# Copiar el contenido del proyecto al contenedor
COPY . /var/www/html/
WORKDIR /var/www/html/



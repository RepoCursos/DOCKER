FROM php:8.1.0-apache
WORKDIR /var/www/html

#Modeo rescritura
RUN a2enmod rewrite

#Librerias de Linux
RUN apt-get update -y && apt-get install -y \
    libicu-dev \
    libmariadb-dev \
    unzip zip \
    zlib1g-dev \
    libpng-dev \
    libjpeg-dev \
    libfreetype6-dev \
    libjpeg62-turbo-dev \
    libpng-dev

#Composer
COPY --from=composer:latest /usr/bin/composer /usr/bin/composer

#Extencione de PHP
RUN docker-php-ext-install gettext intl pdo_mysql gd


RUN docker-php-ext-configure gd --enable-gd --with-freetype --with-jpeg \
    && docker-php-ext-install -j$(nproc) gd


#Luego de instalar Laravel nos fijamos en la pagina con la direccion:
#localhost:8000/public/
#Si da error tenemos que ingresar el siguiente comando dentro del contenedor
#chown -R www-data:www-data /var/www/html

#Para corregir las direccion y que nos quede localhost:8000
#Tenemos que agregar el archivo .htaccess y agregamos lo siguiente
# RewriteEngine On
# RewriteCond %{REQUEST_URI} !^/public/
# RewriteRule ^(.*)$ /public/$1 [L,QSA]

#Luego de hacer estos pasos recordemos que en el archivo .env, el la configuracion de la conexion a la BD
#Tenemos que poner en la linea del HOST 
#DB_HOST=mysql_db "el nombre del contenedor de la BD"

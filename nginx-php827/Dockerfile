FROM php:8.2.7-fpm
# FROM public.ecr.aws/docker/library/php:8.2.7-fpm

RUN apt-get update && apt-get install -y \
    nginx \
    zip \
    unzip \
    git \
    curl \
    libpng-dev \
    libonig-dev \
    libxml2-dev \
    libzip-dev

RUN apt-get clean && rm -rf /var/lib/apt/lists/*

RUN docker-php-ext-install pdo_mysql mbstring exif pcntl bcmath gd zip

COPY --from=composer:latest /usr/bin/composer /usr/bin/composer

WORKDIR /var/www/html

COPY index.php /var/www/html

# Clone CodeIgniter 3.1.13
# RUN git clone https://github.com/bcit-ci/CodeIgniter.git --branch 3.1.13 --single-branch .

# Install CodeIgniter dependencies (if any)
# RUN composer install

COPY nginx.conf /etc/nginx/nginx.conf

COPY www.conf /usr/local/etc/php-fpm.d/www.conf

RUN chown -R www-data:www-data /var/www/html
RUN chmod -R 755 /var/www/html

EXPOSE 80

CMD service nginx start && php-fpm

# CMD ["nginx", "-g", "daemon off;"]
# CMD ["nginx", "-g", "daemon off;"]
# docker buildx build -t server:v1 .

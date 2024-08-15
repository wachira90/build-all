# Dockerfile
# FROM php:8.3-apache
FROM public.ecr.aws/docker/library/php:8.2.7-apache
# SHELL ["/bin/bash", "-c"]
ENV SHELL="/bin/bash"

# Enable mod_rewrite for Apache
RUN a2enmod rewrite

# Install any additional PHP extensions if needed
# RUN docker-php-ext-install pdo_mysql
RUN apt-get update
RUN docker-php-ext-install mysqli

# RUN apk update

RUN docker-php-ext-install pdo_mysql
RUN docker-php-ext-install opcache 
RUN docker-php-ext-install pdo 
RUN docker-php-ext-install calendar
RUN docker-php-ext-install ctype 
RUN docker-php-ext-install exif 
RUN docker-php-ext-install fileinfo 


# RUN docker-php-ext-enable calendar 
# RUN docker-php-ext-enable exif 
RUN docker-php-ext-enable mysqli
# RUN docker-php-ext-enable opcache 
# RUN docker-php-ext-enable pdo_mysql 
# RUN docker-php-ext-enable sodium

# RUN apt-get install libjpeg-turbo-dev libpng-dev libwebp-dev freetype-dev

RUN apt install libjpeg-turbo-progs libjpeg62-turbo libjpeg62-turbo-dev -y
RUN apt install libpng-dev -y

# RUN docker-php-ext-configure gd --enable-gd --with-freetype --with-jpeg

RUN docker-php-ext-configure gd 

RUN docker-php-ext-install gd
# RUN apk add  php-pecl-zip

RUN apt-get install  -y openssl libssl-dev libcurl4-openssl-dev
# RUN pecl install mongodb-1.6.0



# Copy your application code to the container
COPY ./src /var/www/html/

# Set proper permissions
RUN chown -R www-data:www-data /var/www/html/

# Expose port 80
EXPOSE 80

CMD ["/bin/bash"]
# CMD ["/bin/bash", "-c"]
# RUN touch /root/.bashrc

RUN curl -o- https://raw.githubusercontent.com/nvm-sh/nvm/v0.39.1/install.sh | bash
# RUN source /root/.bashrc
# RUN nvm ls-remote 
# RUN nvm install v21.7.3

# RUN /bin/bash
RUN nvm install v21.7.3

# docker build -t apache2-php83:v1 .

# docker build -t wachiradu/apache2-php827:v1 .
# docker build -t wachiradu/apache2-php827:v2 .
# docker build -t wachiradu/apache2-php827:v3 .

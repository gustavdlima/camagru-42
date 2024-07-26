FROM php:8.2-apache

# Install dependencies
RUN apt-get update && apt-get install -y \
	libfreetype-dev \
	libjpeg62-turbo-dev \
	libpng-dev \
	&& docker-php-ext-configure gd --with-freetype --with-jpeg \
	&& docker-php-ext-install -j$(nproc) gd

# Clean
RUN apt-get clean && rm -rf

# Set working directory
WORKDIR /var/www/html

# Active Apache rewrite module
RUN a2enmod rewrite

# Copy source code
COPY src/ .

# Permissions
RUN chown -R www-data:www-data /var/www/html

# Expose port 80
EXPOSE 80

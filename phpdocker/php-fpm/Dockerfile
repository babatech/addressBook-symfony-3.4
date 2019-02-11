FROM php:7.0-fpm
WORKDIR "/application"

# Fix debconf warnings upon build
ARG DEBIAN_FRONTEND=noninteractive

# apt update
RUN apt-get update

# Install git
RUN apt-get -y install git

# Install Composer dependices
RUN apt-get -y install curl nano && \
        curl -sS https://getcomposer.org/installer | php -- --install-dir=/usr/local/bin --filename=composer


# Install Composer
RUN curl -sS https://getcomposer.org/installer | php -- --install-dir=/usr/local/bin --filename=composer

# Install app dependencies
RUN COMPOSER_ALLOW_SUPERUSER=1 /usr/local/bin/composer install --prefer-source --no-interaction

# Cleanup
RUN apt-get clean; rm -rf /var/lib/apt/lists/* /tmp/* /var/tmp/* /usr/share/doc/*
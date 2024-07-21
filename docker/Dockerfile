FROM ubuntu:24.04

# Install required packages
RUN apt-get update && apt-get install -y \
    apache2 \
    libapache2-mod-php \
    vim \
    zip \
    libzip-dev \
    unzip \
    libpng-dev \
    zlib1g-dev \
    libxml2-dev \
    curl \
    gnupg \
    wget \
    git \
    xz-utils

# Set timezone to Japan
RUN ln -sf /usr/share/zoneinfo/Asia/Tokyo /etc/localtime \
    && echo "Asia/Tokyo" > /etc/timezone \
    && dpkg-reconfigure -f noninteractive tzdata

# Install Node.js
RUN curl -fsSL https://nodejs.org/dist/v16.15.1/node-v16.15.1-linux-x64.tar.xz | tar -xJ \
    && cp -R node-v16.15.1-linux-x64/* /usr/local/ \
    && rm -rf node-v16.15.1-linux-x64

# Set working directory
WORKDIR /var/www

# Start Apache
CMD ["apachectl", "-D", "FOREGROUND"]
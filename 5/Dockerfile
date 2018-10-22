FROM php:5

# Install composer
COPY ./composer-install /tmp/
RUN /tmp/composer-install && rm /tmp/composer-install

# Install additional components
RUN apt-get update && apt-get install -y \
        libfreetype6-dev \
        libjpeg62-turbo-dev \
        libpng-dev \
    && docker-php-ext-install -j$(nproc) iconv \
    && docker-php-ext-configure gd --with-freetype-dir=/usr/include/ --with-jpeg-dir=/usr/include/ \
    && docker-php-ext-install -j$(nproc) gd \
    && docker-php-ext-install exif

RUN useradd --uid 1000 --gid users --shell /bin/bash --create-home phpuser

WORKDIR /var/www/html

USER phpuser
CMD ["bash"]

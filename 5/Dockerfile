FROM php:5

# Install composer
COPY ./composer-install /tmp/
RUN /tmp/composer-install && rm /tmp/composer-install

RUN useradd --uid 1000 --gid users --shell /bin/bash --create-home phpuser

WORKDIR /var/www/html

USER phpuser
CMD ["bash"]

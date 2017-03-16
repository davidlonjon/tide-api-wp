#
#--------------------------------------------------------------------------
# Image Setup
#--------------------------------------------------------------------------
#

FROM wordpress:4.7-php7.0-fpm

MAINTAINER David Lonjon <david.lonjon@xwp.co>

RUN docker-php-ext-install -j$(nproc) pdo && \
        docker-php-ext-install -j$(nproc)  pdo_mysql

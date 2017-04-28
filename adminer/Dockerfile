FROM adminer:4.3.0

# Version 4.3.1 contains PostgreSQL login errors. See docs.
# See https://sourceforge.net/p/adminer/bugs-and-features/548/

MAINTAINER Patrick Artounian <partounian@gmail.com>

USER root

# Store PHP Configs at /usr/local/etc/php/conf.d
RUN echo "upload_max_filesize = 2000M" >> /usr/local/etc/php/conf.d/upload_large_dumps.ini \
    && echo "post_max_size = 2000M" >> /usr/local/etc/php/conf.d/upload_large_dumps.ini \
    && echo "memory_limit = -1" >> /usr/local/etc/php/conf.d/upload_large_dumps.ini \
    && echo "max_execution_time = 0" >> /usr/local/etc/php/conf.d/upload_large_dumps.ini

# Set Adminer Default Theme
COPY adminer.css /var/www/html/adminer.css

# Set plugins
COPY plugins /var/www/html/plugins/

# Set index.php
COPY index.php /var/www/html/index.php

# Add volume for sessions to allow session persistence
VOLUME /sessions

USER adminer

# We expose Adminer on port 8080 (Adminer's default)
EXPOSE 8080

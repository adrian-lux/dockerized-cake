FROM php:5.6-apache

ENV DEBIAN_FRONTEND noninteractive

RUN apt-get update \
  && apt-get install -y libfreetype6-dev libjpeg62-turbo-dev libpng-dev libmcrypt-dev apache2-bin curl git vim  libxml2-dev libicu-dev elinks\
  && docker-php-ext-install pdo_mysql mysqli mbstring mcrypt gd iconv zip xml intl

RUN yes | pecl install xdebug-2.5.5 \
    && echo "zend_extension=$(find /usr/local/lib/php/extensions/ -name xdebug.so)" > /usr/local/etc/php/conf.d/xdebug.ini \
    && echo "xdebug.remote_enable=on" >> /usr/local/etc/php/conf.d/xdebug.ini \
    && echo "xdebug.remote_autostart=off" >> /usr/local/etc/php/conf.d/xdebug.ini

RUN echo "xdebug.idekey = PHPSTORM" >> /usr/local/etc/php/conf.d/xdebug.ini
RUN echo "xdebug.default_enable = 0" >> /usr/local/etc/php/conf.d/xdebug.ini
RUN echo "xdebug.remote_enable = 1" >> /usr/local/etc/php/conf.d/xdebug.ini
RUN echo "xdebug.remote_autostart = 0" >> /usr/local/etc/php/conf.d/xdebug.ini
RUN echo "xdebug.remote_connect_back = 0" >> /usr/local/etc/php/conf.d/xdebug.ini
RUN echo "xdebug.profiler_enable = 0" >> /usr/local/etc/php/conf.d/xdebug.ini
RUN echo "xdebug.remote_host = 10.254.254.254" >> /usr/local/etc/php/conf.d/xdebug.ini

# Set environmental variables
ENV COMPOSER_HOME /root/composer
# Install Composer
RUN curl -sS https://getcomposer.org/installer | php -- --install-dir=/usr/local/bin --filename=composer

ADD ./php.ini /usr/local/etc/php/php.ini

ADD ./default.conf /etc/apache2/sites-available/000-default.conf

ENV APACHE_RUN_USER www-data
ENV APACHE_RUN_GROUP root
ENV APACHE_LOG_DIR /var/log/apache2
ENV APACHE_PID_FILE /var/run/apache2.pid
ENV APACHE_RUN_DIR /var/run/apache2
ENV APACHE_LOCK_DIR /var/lock/apache2

RUN mkdir -p $APACHE_RUN_DIR $APACHE_LOCK_DIR $APACHE_LOG_DIR
RUN a2enmod rewrite

#RUN composer install

CMD ["apache2", "-D", "FOREGROUND"]
RUN /bin/bash chown -R www-data /var/www/html/cakephp/app/tmp

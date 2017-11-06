FROM php:7.1-fpm

RUN apt-get update \
    && apt-get install -y wget \
    && echo 'deb http://packages.dotdeb.org jessie all' >> /etc/apt/sources.list \
    && echo 'deb-src http://packages.dotdeb.org jessie all' >> /etc/apt/sources.list \
    && wget https://www.dotdeb.org/dotdeb.gpg \
    && apt-key add dotdeb.gpg \
    && apt-get update \
    && apt-get install -y php7.0-dev zip unzip libmcrypt-dev mysql-client git tree --no-install-recommends \
    && docker-php-ext-install zip mcrypt pdo_mysql \
    && rm -rf /var/lib/apt/lists/*

COPY php.7.1.2.ini /usr/local/etc/php
COPY config/gitconfig /root/.gitconfig

RUN pecl install xdebug-2.5.0 \
  && docker-php-ext-enable xdebug

RUN php -r "copy('https://getcomposer.org/installer', 'composer-setup.php');" \
  && php -r "if (hash_file('SHA384', 'composer-setup.php') === '544e09ee996cdf60ece3804abc52599c22b1f40f4323403c44d44fdfdd586475ca9813a858088ffbc1f233e9b180f061') { echo 'Installer verified'; } else { echo 'Installer corrupt'; unlink('composer-setup.php'); } echo PHP_EOL;" \
  && php composer-setup.php \
  && mv composer.phar /usr/local/bin/composer \
  && php -r "unlink('composer-setup.php');"

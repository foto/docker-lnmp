# 基础镜像
FROM php:7.4.6-fpm
#FROM php:7.1.6-fpm
#FROM php:7.2.6-fpm

ARG SWOOLE_VERSION=4.5.9
ARG XDEBUG_VERSION=2.7.1
ENV TZ=Asia/Shanghai

RUN ln -snf /usr/share/zoneinfo/$TZ /etc/localtime && echo $TZ > /etc/timezone \
    && echo "net.core.somaxconn=20480" >> /etc/sysctl.conf \
    && apt-get update \
    && apt-get install -y libzip-dev \
    && apt-get install -y libfreetype6-dev libjpeg62-turbo-dev libmcrypt-dev  libwebp-dev libjpeg-dev libpng-dev  libpng-dev wget  libmemcached-dev zlib1g-dev \
    && docker-php-ext-install -j$(nproc) iconv \
    && docker-php-ext-install pdo_mysql \
    && docker-php-ext-install zip \
    && docker-php-ext-install bcmath \
    && pecl install redis \
    && docker-php-ext-enable redis \
    && docker-php-ext-install mysqli \
    # && docker-php-ext-configure gd --with-webp-dir=/usr/include/webp --with-jpeg-dir=/usr/include --with-png-dir=/usr/include --with-freetype-dir=/usr/include/freetype2  \
    # && docker-php-ext-install gd \
    && cd ~ \
    && php -r "copy('https://install.phpcomposer.com/installer', 'composer-setup.php');" \
    && php composer-setup.php \
    && mv composer.phar /usr/local/bin/composer


#    RUN  cd ~ \
#        && wget https://github.com/swoole/swoole-src/archive/v$SWOOLE_VERSION.tar.gz \
#        && tar -zxf v$SWOOLE_VERSION.tar.gz \
#        && rm v$SWOOLE_VERSION.tar.gz \
#        && mkdir -p /usr/src/php/ext/ \
#        && mv swoole-src-$SWOOLE_VERSION /usr/src/php/ext/swoole \
#        && docker-php-ext-install swoole \
#        && rm -rf /usr/src/php/ext/swoole
#
#    RUN  cd ~ \
#        && wget https://github.com/xdebug/xdebug/archive/$XDEBUG_VERSION.tar.gz \
#        && tar -zxf $XDEBUG_VERSION.tar.gz \
#        && rm $XDEBUG_VERSION.tar.gz \
#        && mv xdebug-$XDEBUG_VERSION  /usr/src/php/ext/xdebug \
#        && cd /usr/src/php/ext/xdebug  \
#        && phpize \
#        && ./configure --enable-xdebug \
#        && docker-php-ext-install xdebug

COPY ./config/php2.ini /usr/local/etc/php/conf.d/

CMD ["/usr/local/sbin/php-fpm", "-F"]

EXPOSE 9000



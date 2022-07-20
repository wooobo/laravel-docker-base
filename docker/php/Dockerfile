FROM php:fpm

# Timezone 설정
ENV TZ Asia/Seoul

# Yarn 설치
RUN apt-get update --fix-missing \
    && apt-get install -y --no-install-recommends nodejs npm \
    && npm install -g yarn

# Composer 설치
RUN php -r "copy('https://getcomposer.org/installer', 'composer-setup.php');" \
    && php composer-setup.php --install-dir=/usr/local/bin --filename=composer \
    && php -r "unlink('composer-setup.php');"

# 필요 패키지 설치
RUN apt-get update --fix-missing \
    && apt-get install -y --no-install-recommends git \
    zlib1g-dev \
    libonig-dev \
    curl && apt-get clean

#RUN docker-php-ext-install bcmath \
#    mysqli \
#    pdo_mysql \
#    gd \
#    zip \
#    exif \
#    calendar \
#    iconv \
#    intl \
#    pdo \
#    pcntl \
#    tokenizer \
#    xml

# PHP 확장 모듈 설치
RUN pecl install -o -f redis \
    && pecl install xdebug \
    && docker-php-ext-enable xdebug

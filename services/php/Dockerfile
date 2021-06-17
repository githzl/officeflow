ARG PHP_IMAGE_VERSION
FROM ${PHP_IMAGE_VERSION}


ARG TZ
COPY ./extensions /tmp/extensions
WORKDIR /tmp/extensions

# redis 
# RUN tar -xzf redis-3.1.2.tgz \
#     && docker-php-source extract \
#     && mv redis-3.1.2 /usr/src/php/ext/phpredis \
#     && docker-php-ext-install phpredis \
#     && docker-php-ext-enable redis \
#     && docker-php-source delete

# yaml 先安装libyaml再安装php的yaml
# RUN apk --update add --no-cache gcc libc-dev make \ 
#     # libyaml 依赖gcc libc-dev make
#     && tar -xzvf yaml-0.1.4.tar.gz \
#     && ./yaml-0.1.4/configure --prefix=/usr/local \
#     && make \
#     && make install \ 
#     # 开始安装php yaml扩展
#     && tar -zxvf yaml-2.0.4.tgz \
#     && docker-php-source extract \
#     && mv yaml-2.0.4 /usr/src/php/ext/yaml \
#     && docker-php-ext-install yaml \
#     && docker-php-ext-enable yaml \
#     && docker-php-source delete \
#     && rm -rf /tmp

# pdo_pgsql
# RUN apk --update add --no-cache postgresql-dev \
#     && docker-php-source extract \
#     && docker-php-ext-install pdo_pgsql \
#     && docker-php-ext-enable pdo_pgsql \
#     && docker-php-source delete

# exif
# docker-php-source extract \
#    && docker-php-ext-install exif \
#    && docker-php-ext-enable exif \
#    && docker-php-source delete

# gd
# RUN apk --update add --no-cache libpng-dev libpng libwebp libwebp-dev libjpeg-turbo-dev freetype-dev \
#     && docker-php-source extract \
#     && docker-php-ext-configure gd --with-webp-dir=/usr/include/webp --with-jpeg-dir=/usr/include --with-png-dir=/usr/include --with-freetype-dir=/usr/include/freetype2 \
#     && docker-php-ext-install gd \
#     && docker-php-ext-enable gd \
#     && docker-php-source delete

# iconv 函数无法使用问题
# RUN tar -xzvf libiconv-1.14.tar.gz \
#     && ./libiconv-1.14/configure --prefix=/usr/local/libiconv \
#     # make 如果出现./stdio.h:1010:1: error: 'gets' undeclared here (not in a function)，删除掉1010，1011两行即可
#     && make \
#     && make install \
ENV LD_PRELOAD /usr/local/libiconv/lib/preloadable_libiconv.so php

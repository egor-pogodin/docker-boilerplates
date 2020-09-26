FROM php:7.2-apache

WORKDIR /var/www/html


RUN apt-get update && apt-get install -qq \
        libfreetype6-dev \
        libjpeg62-turbo-dev \
        libmcrypt-dev \
        libxml2-dev \
        libbz2-dev \
        libgmp-dev \
        libc-client-dev \
        libkrb5-dev \
        libldb-dev \
        libldap2-dev \
        libpspell-dev\
        librecode-dev\
        libtidy-dev \
        libxslt1-dev \
    && pecl install mcrypt-1.0.1 \
    && ln -s /usr/lib/x86_64-linux-gnu/libldap.so /usr/lib/libldap.so \
    && ln -s /usr/lib/x86_64-linux-gnu/liblber.so /usr/lib/liblber.so \
    && set -x \
    && docker-php-ext-install \
    	zip \
    	bcmath \
    	bz2 \
    	calendar \
    	exif \
    	gettext \
    	gmp \
    	intl \
    	ldap \
    	# pspell \
    	recode \
    	shmop \
    	sockets \
    	# sysvmsg \
    	# sysvsem \
    	tidy \
    	# wddx \
    	xmlrpc \
    	xsl \
    	pdo_mysql \
    	mysqli \
    	mbstring \
    	opcache \
    	soap > /dev/null \
    && docker-php-ext-configure imap --with-kerberos --with-imap-ssl && docker-php-ext-install imap \
    && docker-php-ext-configure gd --with-freetype-dir=/usr/include/ --with-jpeg-dir=/usr/include/ \
    && docker-php-ext-install gd > /dev/null \
    && docker-php-ext-enable mcrypt \
    && curl -sS https://getcomposer.org/installer | php -- --install-dir=/usr/local/bin --filename=composer 
    # && composer install

RUN a2enmod rewrite
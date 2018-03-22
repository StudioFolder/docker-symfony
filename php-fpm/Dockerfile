FROM php:7.1-fpm
ARG TIMEZONE

RUN apt-get update

RUN apt-get install -y \
  gnupg \
	zlib1g-dev \
	libxml2-dev \
	apt-utils \
  libicu-dev \
  git \
	openssl \
	unzip

# Install Composer
RUN curl -sS https://getcomposer.org/installer | php -- --install-dir=/usr/local/bin --filename=composer
RUN composer --version

# Install node with yarn
RUN curl -sL https://deb.nodesource.com/setup_8.x | bash -
RUN curl -sS https://dl.yarnpkg.com/debian/pubkey.gpg | apt-key add -
RUN echo "deb https://dl.yarnpkg.com/debian/ stable main" | tee /etc/apt/sources.list.d/yarn.list
RUN apt-get update
RUN apt-get install -y \
  nodejs \
  yarn

# Set timezone
RUN ln -snf /usr/share/zoneinfo/${TIMEZONE} /etc/localtime && echo ${TIMEZONE} > /etc/timezone
RUN printf '[PHP]\ndate.timezone = "%s"\n', ${TIMEZONE} > /usr/local/etc/php/conf.d/tzone.ini
RUN "date"

# Install Extensions
RUN docker-php-ext-install intl
RUN docker-php-ext-install zip xml


WORKDIR /var/www/symfony
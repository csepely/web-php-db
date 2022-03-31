FROM php:5.6.40-fpm
RUN apt-get update && \
    apt-get install -y locales && \
    rm -rf /var/lib/apt/lists/* \
    && localedef -i en_US -c -f UTF-8 -A /usr/share/locale/locale.alias en_US.UTF-8 && \
  ln -sf /usr/share/zoneinfo/Europe/Budapest /etc/localtime
ENV LANG=en_US.UTF-8 TZ=Europe/Budapest
RUN curl -sSLf \
        -o /usr/local/bin/install-php-extensions \
        https://github.com/mlocati/docker-php-extension-installer/releases/latest/download/install-php-extensions && \
    chmod +x /usr/local/bin/install-php-extensions && \
    install-php-extensions gd mysql mysqli opcache gettext exif pdo_mysql

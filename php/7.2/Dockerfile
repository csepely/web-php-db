FROM php:7.2-fpm
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
    install-php-extensions \
    exif \
    gd \
    gettext \
    mcrypt \
    mysqli \
    pdo_mysql \
    opcache
RUN set -eux; \
        { \
          echo '[global]'; \
          echo 'daemonize = no'; \
          echo ''; \
          echo '[www]'; \
          echo 'listen = /run/php/php7.2-fpm.sock'; \
          echo 'listen.owner = www-data'; \
          echo 'listen.group = www-data'; \
          echo 'listen.mode = 0660'; \
          echo 'access.format = "%R - %u %t \"%m %r%Q%q\" %s %f %{mili}d %{kilo}M %C%%"'; \
        } > /usr/local/etc/php-fpm.d/zz-docker.conf

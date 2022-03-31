FROM mariadb:latest
RUN apt-get update && \
  apt-get install -y locales && \
  rm -rf /var/lib/apt/lists/* \
    && localedef -i en_US -c -f UTF-8 -A /usr/share/locale/locale.alias en_US.UTF-8 && \
  ln -sf /usr/share/zoneinfo/Europe/Budapest /etc/localtime
ENV LANG=en_US.UTF-8 TZ=Europe/Budapest


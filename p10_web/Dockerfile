FROM alt:p10

# Перед запуском контейнера:
# 1. Расположите php-скрипты в каталог хостовой системы по адресу /var/www/public 

# Установка необходимых пакетов
RUN apt-get update && \
    apt-get install -y \
        apache2-full \
        apache2-mod_php8.2 \
        php8.2 \
        php8.2-gd \
        php8.2-mbstring \
        php8.2-devel \
        php8.2-libs \
        php8.2-pdo \
        php8.2-pdo_pgsql \
        php8.2-pgsql && \
    apt-get clean

# Или если конфиг находится в подкаталоге config:
COPY ./config/httpd.conf /etc/httpd/conf/httpd2.conf

COPY ./html /var/www/html

# Объявляем точку понтирования, будем указывать ее
# в docker run для определения каталога с php-скриптами
VOLUME /var/www/html

# Открываем порт
EXPOSE 80

CMD ["/usr/sbin/httpd2", "-D", "FOREGROUND"]
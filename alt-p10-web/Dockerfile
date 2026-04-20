FROM alt:p10

# [Секция 1]
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

# [Секция 2]. Копирование конфигурационных файлов в контейнер
# Копируем в контейнер файл конфигурации web-сервера Apache 2.
COPY ./config/httpd.conf /etc/httpd/conf/httpd2.conf
COPY ./config/php.ini /etc/php/8.2/cli/php.ini

# Копируем в контейнер каталог html-файлов, для отображения
# диагностической страницы 
COPY ./html /var/www/html

# [Секция 3] Определение точки монтирования
# Объявляем точку монтирования, для случая, если при запуске
# контейнера необходимо будет переопределить каталог 
# с php-скриптами
VOLUME /var/www/html

# [Секция 4]
# Открываем порт
EXPOSE 80

# [Секция 5]
# Запуск целевого сервиса (Apache 2)
CMD ["/usr/sbin/httpd2", "-D", "FOREGROUND"]
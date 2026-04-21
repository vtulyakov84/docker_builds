FROM bitnami/minideb:latest

# Установка переменных окружения
ENV DEBIAN_FRONTEND=noninteractive

# Обновление и установка Apache 2.4 и PHP 8.4
RUN install_packages \
    apache2 \
    apache2-utils \
    php8.4 \
    php8.4-cli \
    php8.4-common \
    php8.4-curl \
    php8.4-gd \
    php8.4-mbstring \
    php8.4-mysql \
    php8.4-pgsql \
    php8.4-xml \
    php8.4-zip \
    php8.4-intl \
    php8.4-bcmath \
    libapache2-mod-php8.4 \
    && apt-get clean \
    && rm -rf /var/lib/apt/lists/*

# Включение модулей Apache
RUN a2enmod php8.4 \
    && a2enmod rewrite \
    && a2enmod headers

# Копирование файлов приложения (при необходимости)
COPY ./html/ /var/www/html/

# Настройка прав
RUN chown -R www-data:www-data /var/www/html && \
    chmod -R 755 /var/www/html

# Открытие порта
EXPOSE 80

# Запуск Apache в foreground режиме
CMD ["/usr/sbin/apache2ctl", "-D", "FOREGROUND"]
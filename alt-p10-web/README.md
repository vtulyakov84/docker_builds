Имя создаваемого образа: `alt-p10-web:1.0.0`

### Фаловая структура проекта
```bash
[user@vbox alt-p10-web]$ tree .
.
├── config
│   ├── httpd.conf
│   └── php.ini
├── html
│   ├── default-styles.css
│   ├── index.html
│   └── phpinfo.php
├── scripts
│   └── index.php
├── Dockerfile
└── README.md

3 directories, 8 files
```
| Путь | Описание |
|------|----------|
| `./config` | **каталог хранения конфигурации** |
| `./config/httpd.conf` | файл конфигурации web-сервера apache |
| `./config/php.ini` | файл конфигурации php8.2 |
| `./html` | **каталог, копируемый в образ по умолчанию** |
| `./html/default-styles.css` | файл стилей |
| `./html/index.html` | отображаемая страница |
| `./html/phpinfo.php` | действующая конфигурация php 8.2 |
| `./scripts/` | **отладочный каталог, для прикрепления во время запуска контейнера** |
| `./scripts/index.php` | исполняемый файл главной страницы |
| `Dockerfile` | сценарий создания образа |
| `README.md` | файл, который Вы сейчас читаете |

Сборка образа из Dockerfile
```bash
# Сборка образа с тегом
$ docker build -t alt-p10-web:1.0.0 .
```

web/Dockerfile
```bash
# Сборка образа
$ docker build -t alt-web:1.0.0 .

# Запуск контейнера, с пробросом портов для работы через 
$ docker run -d -p 8080:80 alt-web:1.0.0

# Подключение к командной строке контейнера
$ docker exec -it alt-web:1.0.0 /bin/bash

# Выяснить хэш-контейнера
$ docker ps

# Остановить контейнер
$ docker stop f8424585287c

# Удалить контейнер
$ docker rmi f8bce3b535bd -f
```

```bash
# Запуск контейнера с пробросом порта на все интерфейсы хоста
# , чтобы была возможность подключаться к нему с других компьютеров
# в сети
docker run -p 0.0.0.0:8080:80 alt-web:1.0.0

# Или сокращенно (что то же самое по умолчанию)
docker run -p 8080:80 alt-web:1.0.0
```
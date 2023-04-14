FROM ubuntu

# Установка Apache
RUN apt-get update -y && \
    apt-get install -y apache2

# Установка MySQL
RUN apt-get install -y mysql-server

# Копирование конфигурационных файлов
COPY apache-config.conf /etc/apache2/sites-available/000-default.conf
COPY mysql-config.cnf /etc/mysql/mysql.conf.d/mysqld.cnf

# Копирование файлов в директории Apache и MySQL
COPY index.html /var/www/html/
COPY sample-db.sql /docker-entrypoint-initdb.d/

# Открытие портов
EXPOSE 80
EXPOSE 3306

# Запуск команды при запуске контейнера
CMD service mysql start && /usr/sbin/apache2ctl -D FOREGROUND

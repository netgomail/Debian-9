### Настройка и оптимизация сервера под Битрикс
Установка Apache2 и MySQL
```
# apt-get install apache2 apache2-doc && apt-get install mysql-server
# mysql_secure_installation
```
Установка PHP
```
# apt-get install php5-common libapache2-mod-php5 php5-cli
# apt-get install php5-gd php5-mysql php5-mcrypt libssl-dev openssl memcached php5-memcache
```
Установка Nginx
```
# service apache2 stop
# apt-get install nginx libapache2-mod-rpaf
```
#### Создание виртуальных хостов
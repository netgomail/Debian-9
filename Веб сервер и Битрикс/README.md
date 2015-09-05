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
Создаем папки где будут находится сайты, сам сайт закачивать в папку public_html
```
# mkdir -p /var/www/{site.loc,site2.loc}/{public_html,logs,cgi,other,tmp}
```
Меняем права на созданные папки, а так же на файлы в каталогах (файлы 644, папки 755)
```
# find /var/www -type f -exec chmod 644 {} \; 
# find /var/www -type d -exec chmod 755 {} \;
```
Меняем пользователя на имя от которого работает Apache
```
chown -R www-data:www-data /var/www
```
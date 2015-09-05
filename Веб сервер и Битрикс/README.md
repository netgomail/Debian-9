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
#### Структура каталогов с сайтами
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
Добавляем в /etc/hosts наши сайты
```
127.0.0.1	site.loc
127.0.0.1	site2.loc
```
### apache
Так как апач будет работать в свзяке с nginx, меняем порты у апача

В /etc/apache2/ports.conf меняем `Listen 80` на:
```
Listen 127.0.0.1:8887
NameVirtualHost 127.0.0.1:8887
```
Создать хост 
- /etc/apache2/sites-available/[site.conf](https://github.com/netgomail/Debian-9/blob/master/%D0%92%D0%B5%D0%B1%20%D1%81%D0%B5%D1%80%D0%B2%D0%B5%D1%80%20%D0%B8%20%D0%91%D0%B8%D1%82%D1%80%D0%B8%D0%BA%D1%81/site.conf)

Активировать хост
```
# a2ensite site.conf
```
### nginx
Создать хост 
- /etc/apache2/sites-available/[site.conf](https://github.com/netgomail/Debian-9/blob/master/%D0%92%D0%B5%D0%B1%20%D1%81%D0%B5%D1%80%D0%B2%D0%B5%D1%80%20%D0%B8%20%D0%91%D0%B8%D1%82%D1%80%D0%B8%D0%BA%D1%81/site.conf)
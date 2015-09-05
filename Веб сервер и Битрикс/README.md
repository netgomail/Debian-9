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
Снять ограничение на размер стека pcre.recursion_limit

Добавить в файл `/etc/init.d/apache2` строчку `ulimit -s unlimited`.Далее делаем рестарт демона и апача:
```
# systemctl daemon-reload
# service apache2 restart
```

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
- /etc/nginx/sites-available/[site.loc](https://github.com/netgomail/Debian-9/blob/master/%D0%92%D0%B5%D0%B1%20%D1%81%D0%B5%D1%80%D0%B2%D0%B5%D1%80%20%D0%B8%20%D0%91%D0%B8%D1%82%D1%80%D0%B8%D0%BA%D1%81/site.loc)

Активировать хост
```
# ln -s /etc/nginx/sites-available/site.loc /etc/nginx/sites-enabled/site.loc
```
nginx.conf
```
client_max_body_size 12m;
```
### php.ini
- /etc/php5/apache2/php.ini
```
short_open_tag = On
opcache.revalidate_freq=0
memory_limit = 384M
max_input_vars = 12000
upload_max_filesize = 8M
```
### mysql
- /etc/mysql/my.cnf

```
innodb_buffer_pool_size=250M 
innodb_additional_mem_pool_size=50M 
innodb_file_io_threads=8 
innodb_lock_wait_timeout=50 
innodb_log_buffer_size=8M 
innodb_flush_log_at_trx_commit=0 
```
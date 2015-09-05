#### Изменить /etc/apt/sources.list

```
deb http://ftp.ru.debian.org/debian stretch main contrib non-free
deb-src http://ftp.ru.debian.org/debian stretch main contrib non-free

deb http://ftp.debian.org/debian/ stretch-updates main contrib non-free
deb-src http://ftp.debian.org/debian/ stretch-updates main contrib non-free

deb http://security.debian.org/ stretch/updates main contrib non-free
deb-src http://security.debian.org/ stretch/updates main contrib non-free
```

##### Выполнить команду в терминале
```
apt-get update && apt-get dist-upgrade
```

### Команды

Установка пакета

```# dpkg -i package.deb```

Установка зависимостей для пакета

```apt-get -f install```
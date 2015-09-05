#### Изменить /etc/apt/sources.list

```
deb http://mirror.yandex.ru/debian/ stretch main contrib non-free
deb-src http://mirror.yandex.ru/debian/ stretch main contrib non-free

deb http://mirror.yandex.ru/debian/ stretch-updates main contrib non-free
deb-src http://mirror.yandex.ru/debian/ stretch-updates main contrib non-free

deb http://mirror.yandex.ru/debian-security/ stretch/updates main contrib non-free
deb-src http://mirror.yandex.ru/debian-security/ stretch/updates main contrib non-free
```

##### Выполнить команду в терминале
```
apt-get update && apt-get dist-upgrade
```

### Команды

Установка пакета

```
# dpkg -i package.deb
```

Установка зависимостей для пакета

```
# apt-get -f install
```

Пакетный менеджер, что бы не вводить команды в терминале.Сразу устанавливает зависимости.

```
# apt-get install gdebi
```

### Настройка системы

CPU Driver (non-free репозиторий)

```
# apt-get install intel-microcode
```

##### Настроить сглаживание шрифтов в Debian

Добавляем репозиторий (в отдельный лист fontconfig.list) и ключ

```
# echo 'deb http://ppa.launchpad.net/no1wantdthisname/ppa/ubuntu vivid main' >> /etc/apt/sources.list.d/fontconfig.list
# apt-key adv --keyserver keyserver.ubuntu.com --recv-keys E985B27B
# apt-get update && apt-get install fontconfig-infinality
```
Настройка

```
# cd /etc/fonts/infinality/
# bash infctl.sh setstyle
```
- Выбираем 3 пункт (Linux)

```
# nano /etc/profile.d/infinality-settings.sh
```
- Меняем USE_STYLE="DEFAULT" на USE_STYLE="UBUNTU"
- Выходим из системы и заново заходим. Или перезагружаемся.

##### Установка темы Arc-theme и иконки в стиле MacOS

```
# echo 'deb http://ppa.launchpad.net/noobslab/themes/ubuntu vivid main' >> /etc/apt/sources.list.d/arcmactheme.list
# apt-key adv --keyserver keyserver.ubuntu.com --recv-keys D530E028F59EAE4D
# apt-get update && apt-get install arc-theme mbuntu-y-icons-v5
```
- Настройки -> Диспетчер окон и Внешний вид выбрать установленную тему и иконки
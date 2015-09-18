#### Установка локали ru_RU.CP1251
```
# locale-gen ru_RU.CP1251
# dpkg-reconfigure locales

```
#### Загрузка без задержки в GRUB
Изменить GRUB_TIMEOUT=2 на 0
```
# nano /etc/default/grub

```
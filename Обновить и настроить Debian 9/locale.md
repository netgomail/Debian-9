#### Установка локали ru_RU.CP1251
```
# locale-gen ru_RU.CP1251
# dpkg-reconfigure locales

```
#### Загрузка без задержки в GRUB
Изменить GRUB_TIMEOUT=2 на 0
```
# nano /etc/default/grub
# update-grub
```
#### Установить root пароль
```
# sudo passwd root
```
#### Включить доступ к серверу по паролю по ssh
Меняем на PermitRootLogin yes и PasswordAuthentication yes
```
# nano /etc/ssh/sshd_config
# service ssh restart
```
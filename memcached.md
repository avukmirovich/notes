Memcached
==
`http://memcached.org` - официальный сайт

`11211` - порт по-умолчанию
### Установка
`sudo apt-get install memcached php5-memcached`
* `memcached` - сам сервер
* `php5-memcached` - модуль для PHP

### Проверка работы
`echo "stats settings" | nc localhost 11211`

### Настройка
```
sudoedit /etc/memcached.conf
sudo service memcached restart
```

Redis
==
Key-value storage with optional persistent.

`http://redis.io` - официальный сайт

`6379` - порт по-умолчанию

### Установка
`sudo apt-get install redis-server php5-redis`
* `redis-server` - сам сервер
* `php5-redis` - модуль для PHP

### Консольный клиент
```
redis-cli
```
* `info` - информация
* `exit` - выход

### Настройка
```
sudoedit /etc/redis/redis.conf
sudo service redis-server restart
```

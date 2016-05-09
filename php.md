`php5enmod` и `php5dismod` - позволяют активировать и деактивировать модули
`php5query -M` - отображает список активных модулей

`file_get_contents('php://input');` - Получение тела POST-запроса

Package Managers
==
`PEAR` - download and update PHP components
`Composer` - PHP dependency manager. Composer more popular that PEAR
`PECL` - repo for PHP extentions, share PEAR infrastructure. Downloads C-code and compiles it.

Composer
--

### Установка
`curl -sS https://getcomposer.org/installer | php`
###### Доступ для всех пользователей
`sudo mv composer.phar /usr/local/bin/composer`
###### Проверка, что работает
`composer about`
###### Обновление
`composer selfupdate`
###### Чтобы мог загружать в домашнюю папку
```
sed -i '1i export PATH="$HOME/.composer/vendor/bin:$PATH"' $HOME/.bashrc
source $HOME/.bachrc
```

PEAR
--
### Установка
`sudo apt-get install php-pear php5-dev`

XDebug
==
### Установка
`sudo apt-get install php5-xdebug`
### Активация модуля
```
sudo php5enmod xdebug
sudo service apache2 restart
```
### Деактивация модуля
```
sudo php5dismod xdebug
sudo service apache2 restart
```
### Включение профайлера
`sudoedit /etc/php5/mod-available/xdebug.ini`
###### Добавить параметры
```ini
xdebug.profiler_enable_trigger = 1
xdebug.profiler_output_dir = /tmp/cachegrind
```
###### Содание каталога
`mkdir /tmp/cachegrid`
###### Настройка прав доступа
`sudo chown www-data: /tmp/cachegrid` - даем права пользователю, под которым запущен веб-сервер

Graphviz
==
Визуализирует графику из данных профайлера
### Установка
`sudo apt-get install graphviz`

Webgrind
==
### Установка
`git clone https://github.com/jokkedk/webgrind.git`
### Настройка
`nano webgrind/config.php`
```
$profilerDir = '/tmp/cachegrind';
$defaultTimezone = 'Asia/Irkutsk';
$dotExecutable = '/usr/bin/dot';
```

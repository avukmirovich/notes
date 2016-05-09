Gitolite
==
### Установка
`sudo apt-get install gitolite`

### Настройка
`sudo adduser --system --shell /bin/bash --gecos 'Git SCM' --group --disable-password git` - добавляем пользователя `git`

`ssh-keygen -t rsa` - генерируем ssh-ключ для текущего пользователя

`cp ~/.ssh/id_rsa.pub /tmp/local.pub` - копируем публичный ключ в доступное всем место

`sudo -Uu git gl-setup /tmp/local.pub` - конфигурирование

Выбрать `nano` как редактор и:
* раскомментировать `$WEB_INTERFACE` (`gitweb` - нормально)
* `$GITWEB_URI_ESCAPE = 1;`
* `$REPO_UMASK = 0027;`
* `$GL_GITCONFIG_KEYS = "gitweb\.(owner|description|category)*";`

`rm /tmp/local.pub` - удаляем ранее скопированный публичный ключ

`git clone git@locahost:gitolite-admin` - клонируем конфиругационный репозитарий

`cd gitolite-admin` - переходит в директорию

`cat ~/.ssh/authorized_keys >> keydir/<username>.pub` - добавляем ssh-ключ текущего пользователя

###### Редактирование настроек
* `nano conf/gitolite.conf`
* настраиваем права доступа и создаем новые репозитарии
* коммитим
* пушим

GitWeb
--
### Установка
`sudo apt-get install gitweb highlight`
* `highlight` - для подсветки синтаксиса

### Настройка
`sudoedit /etc/gitweb.conf`

* `$projectroot="/home/git/repositories";`
* `$projects_list="/home/git/projects.list";`
* `$feature{'highlight'}{'default'} = [1];` - добавить

`sudoedit /etc/apache2/conf-available/gitweb.conf` - создаем конфигурационный файл для Apache

`sudo usermod -aG git www-data` - добавляем пользователя `git` в группу `www-data`

`sudo chmod g+r /home/git/projects.list` - делаем файл `project.list` доступным для чтения группе `www-data`

`sudo a2enconf gitweb` - активируем новый конфигурационный файл для Apache

`sudo a2enmod cgi` - активируем поддежку `cgi` для Apache

`sudo service apache2 restart` - перезапускаем Apache

###### Разрешаем, какие репозитарии показывать
* переходим в ранее склонированный репозитарий gitolite-admin
* `nano conf/gitolite.conf` - у каждого репозитария, который хотим выставить в `gitweb` добавляем:
 * `R=gitweb`
 * `config gitweb.description="<описание репозитария>"`
* коммитим и пушим

### Тема для diff'а
* `cd /usr/share/gitweb`
* `sudo mv static origin` - делаем резервную копию оригинальной темы
* `sudo git clone git://github.com/kogakure/gitweb-theme.git static`

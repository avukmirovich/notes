etckeeper
==
### Установка
`sudo apt-get install etckeeper`

### Настройка
`sudoedit /etc/etckeeper/etckeeper.conf`
* `VCS=git` - раскомментировать
* `VCS=bzr` - закомментировать
* `PUSH_REMOTE="origin"` - добавить в конце файла

######  Настройка root'а, чтобы он мог коммитить
* `sudo su` - зашли под `root`'ом
* `ssh-keygen -t rsa` - генерируем ключ с параметрами по-умолчанию
* `cp ~/.ssh/id_rsa.pub ~<username>/gitolite-admin/keydir/root.pub` - копируем публичный ключ в склонированный конфигурационный репозитарий `gitolite`'а. `<username>` заменить на имя пользователя, под которым ранее был склонирован конфигурационный репозитарий
* `chown <username>:<username> ~<username>/gitolite-admin/keydir/root.pub` - меняем владельца у только что скопированного файла. `<username>` заменить на имя пользователя, под которым ранее был склонирован конфигурационный репозитарий
* `exit` - выходим из-под `root`'а
* коммитим и пушим

###### Настройка git под root'ом
* `sudo su`
* `git config --global user.email root@local.dev` - указать почту `root`'а, лучше всего домен указать аналочиный имени сервера
* `git config --global user.name Root`
* `git config --global push.default simple`
* `exit`

###### Настройка репозитария в /etc
* `sudo su`
* `cd /etc`
* `etckeeper init`
* `git remote add origin git@localhost:etckeeper.git` - или указать репозитарий на другом `git`-хостинге
* `etckeeper commit "msg"`
* `exit`

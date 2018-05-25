# note-mysql
note-mysql is a sample database to try note-api.

## Example of note-api

[note-api-by-crystal](https://github.com/shiba-hiro/note-api-by-crystal.git)


## Requirements
[Vagrant](https://www.vagrantup.com/)

## Quick start

Execute below command, then virtual machine starts and install mysql, create table.
```
$ git clone https://github.com/shiba-hiro/note-mysql.git
$ cd note-mysql
$ vagrant up
```


If [Docker](https://www.docker.com/) is available, below command will work instead of vagrant.
```
$ git clone https://github.com/shiba-hiro/note-mysql.git
$ cd note-mysql
$ sudo docker run -dt -p 3306:3306 -v $PWD/data/init.sql:/docker-entrypoint-initdb.d/init.sql -e MYSQL_ALLOW_EMPTY_PASSWORD=yes --name note-mysql mysql
```

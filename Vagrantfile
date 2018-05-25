# -*- mode: ruby -*-
# vi: set ft=ruby :

Vagrant.configure("2") do |config|
  config.vm.box = "ubuntu/xenial64"

  config.vm.network "forwarded_port", guest: 3306, host: 3306

  config.vm.synced_folder "./data", "/home/vagrant/data", create: true, owner: "vagrant", group: "vagrant"

  config.vm.provision "shell", inline: <<-SHELL
    sudo apt update

    sudo debconf-set-selections <<< "mysql-server-5.7 mysql-server/root_password password password"
    sudo debconf-set-selections <<< "mysql-server-5.7 mysql-server/root_password_again password password"
    sudo apt install -y mysql-server-5.7
    sudo service mysql stop
    echo 'enable to access from outside'
    sudo sed -i -e 's/bind-address/# bind-address/' /etc/mysql/mysql.conf.d/mysqld.cnf
    echo 'enable to see the query log'
    sudo sed -i -e 's/#general_log/general_log/' /etc/mysql/mysql.conf.d/mysqld.cnf
    echo 'location of log file is...'
    cat /etc/mysql/mysql.conf.d/mysqld.cnf | grep general_log_file
    sudo service mysql start

    mysql -u root --password=password < /home/vagrant/data/init.sql
  SHELL
end

# Fedora 25 Cloud Provisioning

## Base

    $ sudo dnf group install 'Development Tools'
    $ sudo dnf install vim

## SSH

    $ ssh-keygen -b 2048 -t rsa -C COMMENT

## Nginx

    $ sudo rpm --import http://nginx.org/keys/nginx_signing.key
    $ sudo tee /etc/yum.repos.d/nginx.repo <<EOF
[nginx]
name=nginx repo
baseurl=http://nginx.org/packages/mainline/OS/OSRELEASE/$basearch/
gpgcheck=1
enabled=1
EOF
    $ sudo dnf -y install nginx

## MySQL

    $ sudo dnf install https://dev.mysql.com/get/mysql57-community-release-fc25-9.noarch.rpm
    $ sudo dnf install mysql-community-server
    $ sudo systemctl start mysqld
    $ sudo grep 'temporary password' /var/log/mysqld.log
    $ mysql -u root -p
    > ALTER USER 'root'@'localhost' IDENTIFIED BY 'Abc@2017';

## MongoDB

reference
https://docs.mongodb.com/master/tutorial/install-mongodb-on-red-hat/

    $ sudo tee /etc/yum.repos.d/mongodb-org-3.4.repo <<EOF
[mongodb-org-3.4]
name=MongoDB Repository
baseurl=https://repo.mongodb.org/yum/redhat/\$releasever/mongodb-org/3.4/x86_64/
gpgcheck=1
enabled=1
gpgkey=https://www.mongodb.org/static/pgp/server-3.4.asc
EOF

    $ sudo dnf -y install mongodb-org
    $ sudo semanage port -a -t mongod_port_t -p tcp 27017
    $ sudo systemctl start mongod

## Python(Django, Scrapy, Flask, uWSGI, Gunicorn, Twisted, Tornado)

    $ sudo pip3 install --upgrade pip --index https://pypi.douban.com/simple
    $ sudo pip3 install --upgrade django --index https://pypi.douban.com/simple
    $ sudo pip3 install --upgrade scrapy --index https://pypi.douban.com/simple

PROBLEMS:

* gcc: error: /usr/lib/rpm/redhat/redhat-hardened-cc1: No such file or directory

    $ sudo dnf install redhat-rpm-config

Reference

https://bugs.launchpad.net/openstack-gate/+bug/1424582

* build/tmp.linux-x86_64-3.5/_openssl.c:12:24: fatal error: pyconfig.h: No such file or directory

    $ sudo dnf install python3-devel

Reference

http://stackoverflow.com/questions/40038134/fatal-errorpyconfig-hno-such-file-or-directory-when-pip-install-cryptography

* build/tmp.linux-x86_64-3.5/_openssl.c:434:30: fatal error: openssl/opensslv.h: No such file or directory

    $ sudo dnf install openssl-devel

Reference

None
    
    $ sudo pip3 install --upgrade flask --index https://pypi.douban.com/simple
    $ sudo pip3 install --upgrade uwsgi --index https://pypi.douban.com/simple

## Oracle JDK

Reference

http://www.oracle.com/technetwork/java/javase/downloads/jdk8-downloads-2133151.html
https://www.digitalocean.com/community/tutorials/how-to-install-java-on-centos-and-fedora

    $  wget --no-cookies \
    --no-check-certificate \
    --header "Cookie: gpw_e24=https%3A%2F%2Fwww.oracle.com%2Findex.html; oraclelicense=accept-serurebackup-cookie" https://edelivery.oracle.com/otn-pub/java/jdk/8u121-b13/e9e7ea248e2c4826b92b3f075a80e441/jdk-8u121-linux-x64.rpm

    $ sudo alternatives --config java
    $ sudo alternatives --config javac
    $ sudo sh -c "echo export JAVA_HOME=/usr/java/jdk1.8.0_121 >> /etc/environment"

# Server setup HOWTO

## Linux

## Apache HTTPD

    $ sudo apt-get update
    $ sudo apt-get install apache2
    $ sudo apt-get remove --purge apache2 apache2-bin apache2-utils apache2-data
    $ sudo lsof -i:80
    $ sudo service apache2 status

## Nginx

    $ sudo apt-get update
    $ sudo apt-get install nginx-full
    $ sudo lsof -i:8000
    $ sudo service nginx status

## Tomcat

    $ sudo apt-get update
    $ sudo apt-get install tomcat7
    $ sudo lsof -i:8080
    $ sudo service tomcat7 status

## MySQL

## PostgreSQL

[PostgreSQL for Ubuntu](http://www.postgresql.org/download/linux/ubuntu/)
[Ubuntu help for PostgreSQL](https://help.ubuntu.com/community/PostgreSQL)

PostgreSQL is a powerful object-relational database management system, provided under a flexible BSD-style license.
PostgreSQL contains many advanced features, is very fast and standards compliant.
PostgreSQL has bindings for many programming languages such as C, C++, Python, Java, PHP, Ruby... It can be used to
power anything from simple web applications to massive databases with millions of records.

### Installation

Install with command as below,

    $ sudo apt-get install postgresql postgresql-contrib postgresql-client

### Basic Server Setup

Set the password of the PostgreSQL user(role) called "postgres", otherwise we won't be able to access the server externally.

    $ sudo -u postgres psql postgres

with this command connecting as a role with same name as the local user postgres to the database called "postgres"(first argument to psql).
Set a password for the "postgres" database role using the command:

    \password postgres

and give your password when prompted.
Type Control+D or \q to exit the PostgreSQL prompt.

As the local "postgres" Linux user, we are allowed to connect and manipulate the server using the psql command.

Create database easymanager with command as below,

    $ sudo -u postgres createdb easymanager

Install pgAdmin and activate it(postgresql-contrib must be installed before),

    $ sudo apt-get install pgadmin3

for PostgreSQL 8.4, run the adminpack.sql script, simply type:

    $ sudo -u postgres psql < /usr/share/postgresql/8.4/contrib/adminpack.sql

for PostgreSQL 9.3+ install the adminpack "extension" in the "postgres" database:

    $ sudo -u postgres psql
    CREATE EXTENSION adminpack;


## MongoDB

    $ sudo apt-key adv --keyserver hkp://keyserver.ubuntu.com:80 --recv EA312927
    $ echo "deb http://repo.mongodb.org/apt/ubuntu trusty/mongodb-org/3.2 multiverse" | sudo tee -a /etc/apt/sources.list.d/mongodb-org-3.2.list
    $ sudo apt-get update
    $ sudo apt-get install mongodb-org # or
    $ sudo apt-get install mongodb-org=3.2.6 mongodb-org-server=3.2.6 mongodb-org-shell=3.2.6 mongodb-org-mongos=3.2.6 mongodb-org-tools=3.2.6 # or
    $ echo "mongodb-org hold" | sudo dpkg --set-selections
    $ echo "mongodb-org-server hold" | sudo dpkg --set-selections
    $ echo "mongodb-org-mongos hold" | sudo dpkg --set-selections
    $ echo "mongodb-org-shell hold" | sudo dpkg --set-selections
    $ echo "mongodb-org-tools hold" | sudo dpkg --set-selections

## Python

## Ruby

## PHP

## Django

## Rails

## Struts

## RabbitMQ

    $ echo "deb http://www.rabbitmq.com/debian/ testing main" | sudo tee -a /etc/apt/sources.list.d/rabbitmq.list
    $ wget -O- https://www.rabbitmq.com/rabbitmq-release-signing-key.asc | sudo apt-key add -
    $ sudo apt-get update
    $ sudo apt-get install rabbitmq-server

##

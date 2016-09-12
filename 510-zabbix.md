# Zabbix

##

* 1. Installing repository configuration package

    `$ sudo rpm -ivh http://repo.zabbix.com/zabbix/3.0/rhel/7/x86_64/zabbix-release-3.0-1.el7.noarch.rpm`

* 2. Installing Zabbix packages

Install Zabbix packages.

Example for Zabbix server and web frontend with MySQL database(default):

    `$ sudo dnf install zabbix zabbix-server zabbix-web`

Example for installing Zabbix agent only:

    `$ sudo dnf install zabbix-agent`

* 3. Creating initial database

Create Zabbix database and user on MySQL. For instructions on doing that, see [database creation scripts](https://www.zabbix.com/documentation/3.0/manual/appendix/install/db_scripts) for MySQL.

Then import initial schema and data:

    `$ cd /usr/share/doc/zabbix-server-mysql-3.0.0`
    `$ zcat create.sql.gz | mysql -u root -p zabbix`

* 4. Starting Zabbix server process

Edit database configuration in zabbix_server.conf:

    `$ sudo vim /etc/zabbix/zabbix_server.conf`
```
DBHost=localhost
DBName=zabbix
DBUser=zabbix
DBPassword=zabbix
```

Start Zabbix server process:

    `$ sudo systemctl start zabbix-server`

* 5. Editing PHP configuration for Zabbix frontend

Apache configuration file for Zabbix frontend is located in /etc/httpd/conf.d/zabbix.conf. Some PHP settings are already configured.

```
php_value max_execution_time 300
php_value memory_limit 128M
php_value post_max_size 16M
php_value upload_max_filesize 2M
php_value max_input_time 300
php_value always_populate_raw_post_data -1
# php_value date.timezone Europe/Riga
```

It's necessary to uncomment the "date.timezone" setting and set the right timezone for you. After changing the configuration file restart the Apache web server:

    `$ sudo systemctl restart httpd`

Zabbix frontend is available at http://zabbix-fontend-hostname/zabbix in the browser. Default username/password is Admin/zabbix.

## Install from source

    $ sudo dnf -y --enablerepo=mysql57-community-source install mysql-community-devel
    $ sudo dnf -y install net-snmp-devel libcurl-devel libxml2-devel
    $ ./configure --prefix=/usr/local/zabbix --enable-server --enable-agent --with-mysql --with-net-snmp --with-libcurl --with-libxml2
    $ make
    $ sudo make install 

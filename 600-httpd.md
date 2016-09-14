#


##

http://httpd.apache.org/
http://httpd.apache.org/docs/2.4/


##

http://httpd.apache.org/docs/2.4/install.html

    $ lynx http://httpd.apache.org/download.cgi
    $ tar xzf httpd-2.4.23.tar.gz
    $ cd httpd-2.4.23
    $ ./configure --prefix=/usr/local/apache2
    $ make
    $ sudo make install
    $ vim /usr/local/apache2/conf/httpd.conf
    $ /usr/local/apache2/bin/apachectl -k start

NOTE:
http://apr.apache.org/
http://www.pcre.org/


##

    $ sudo dnf install httpd
    $ sudo firewall-cmd --permanent --add-port=80/tcp
    $ sudo firewall-cmd --permanent --add-port=443/tcp
    $ sudo firewall-cmd --reload
    $ sudo systemctl enable httpd.service
    $ sudo systemctl start httpd.service

#

Generally, execute command below to install python package:

    $ sudo pip install --upgrade <package-name>

If something wrong with network, use socks5 proxy instead:

    $ ssh -fN -D 9999 bwg
    $ sudo pip install --proxy socks5://localhost:9999 --upgrade <package-name>

##

django

tornado

requests

Twisted

supervisor

celery

numpy

pandas

scipy

matplotlib

beautifulsoup4

lxml

simplejson

anyjson

scrapy

redis

pyzmq

python-dateutil

virtualenv


##

Install Python 2.7 on CentOS 6.x

https://github.com/h2oai/h2o-2/wiki/Installing-python-2.7-on-centos-6.3.-Follow-this-sequence-exactly-for-centos-machine-only

_CentOS 6.x ships with Python 2.6 and depends on their specific version. Be careful not to replace it or bad things will happen.
If you need access to a newer version of Python you must compile it yourself and install it side-by-side with the system version.

    $ cat /etc/centos-release
    CentOS release 6.8 (Final)

* Install development tools

    $ sudo yum groupinstall "Development tools"

Note: Development environment should be established via this standard way just like `apt-get install build-essential` on Ubuntu.

* Install Python

    $ wget https://www.python.org/ftp/python/2.7.12/Python-2.7.12.tar.xz
    $ tar xJf Python-2.7.12.tar.xz
    $ cd Python-2.7.12
    $ ./configure
    $ make

Python build finished, but the necessary bits to build these modules were not found:
_bsddb, _curses, _curses_panel, _sqlite3, _ssl, _tkinter, bsddb185, bz2, dbm, dl, gdbm, imageop, readline, sunaudiodev, zlib
To find the necessary bits, look in setup.py in detect_modules() for the module's name.

summarized as below:

_bsddb                  --  db4-devel
_curses, _curses_panel  --  ncurses-devel
_sqlite3                --  sqlite-devel
_ssl                    --  openssl-devel
_tkinter                --  tk-devel
bsddb185                --
bz2                     --  bzip2-devel
dbm, gdbm               --  gdbm-devel
dl                      --
imageop                 --
readline                --  readline-devel
sunaudiodev             --
zlib                    --  zlib-devel


    $ sudo yum install openssl-devel ncurses-devel readline-devel sqlite-devel db4-devel gdbm-devel bzip2-devel zlib-devel tk-devel
    $ make
    $ sudo make altinstall

OK, now we have an alternative Python installed without interferring the builtin version one, however, usually we still want to install package manager for Python: pip

    $ wget https://boostrap.pypa.io/ez_setup.py | sudo /usr/local/bin/python2.7
    $ sudo /usr/local/bin/easy_install-2.7 pip
    $ sudo /usr/local/bin/pip-2.7 install ansible -i https://pypi.douban.com/simple
    $ sudo /usr/local/bin/pip-2.7 install django -i https://pypi.douban.com/simple

It is important to use altinstall istead of install, otherwise you will end up with two different versions of Python in the filesystem both named python.
After installing your newly installed Python interpreter will be available as /usr/local/bin/python2.7 and the system version of Python 2.6 will be available as /usr/bin/python and /usr/bin/python2.6.

* Check Python versions

    $ ls -ltr /usr/{,local/}bin/{python,pip,easy_install}*
ls: cannot access /usr/bin/pip*: No such file or directory
ls: cannot access /usr/bin/easy_install*: No such file or directory
-rwxr-xr-x. 2 root root    4864 Aug 18 15:14 /usr/bin/python
lrwxrwxrwx. 1 root root       6 Oct  3 12:59 /usr/bin/python2 -> python
-rwxr-xr-x. 2 root root    4864 Aug 18 15:14 /usr/bin/python2.6
-rwxr-xr-x. 1 root root     412 Nov 10 16:20 /usr/local/bin/easy_install
-rwxr-xr-x. 1 root root     420 Nov 10 16:20 /usr/local/bin/easy_install-2.7
-rwxr-xr-x. 1 root root     370 Nov 10 16:20 /usr/local/bin/pip
-rwxr-xr-x. 1 root root     372 Nov 10 16:20 /usr/local/bin/pip2
-rwxr-xr-x. 1 root root     376 Nov 10 16:20 /usr/local/bin/pip2.7
-rwxr-xr-x. 1 root root 6294745 Nov 10 16:12 /usr/local/bin/python2.7
-rwxr-xr-x. 1 root root    1687 Nov 10 16:13 /usr/local/bin/python2.7-config


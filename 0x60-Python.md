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

#


##

CouchDB

http://couchdb.apache.org/
http://docs.couchdb.org/en/2.0.0/install/unix.html


dependencies:
- [Erlang OTP (>=R61B03, =>19.x)](http://erlang.org/)
- [ICU](http://icu-project.org/)
- [OpenSSL](http://www.openssl.org/)
- [Mozilla SpiderMonkey(1.8.5)](http://www.mozilla.org/js/spidermonkey/)
- [GNU Make](http://www.gnu.org/software/make/)
- [GNU Compiler Collection](http://gcc.gnu.org/)
- [libcurl](http://curl.haxx.se/libcurl/)
- [help2man](http://www.gnu.org/s/help2man/)
- [Python (>=2.7) for docs](http://python.org/)
- [Python Sphinx(>=1.1.3)](http://pypi.python.org/pypi/Sphinx)

deb-based systems:

    $ sudo apt-get --no-install-recommends -y install \
        build-essential pkg-config erlang \
        libicu-dev libmozjs185-dev libcurl4-openssl-dev

rpm-based systems:

	$ sudo yum install autoconf autoconf-archive automake \
    	curl-devel erlang-asn1 erlang-erts erlang-eunit \
    	erlang-os_mon erlang-xmerl help2man \
    	js-devel-1.8.5 libicu-devel libtool perl-Test-Harness


INSTALL

    $ wget http://mirrors.hust.edu.cn/apache/couchdb/source/1.6.1/apache-couchdb-1.6.1.tar.gz
    $ tar xf apache-couchdb-1.6.1.tar.gz
    $ cd apache-couchdb-1.6.1
    $ ./configure
    $ make
    $ sudo make install

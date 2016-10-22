# Apache Thrift

The Apache Thrify software framework, for scalable cross-language services development, combines a software stack with a code generation engine to build
services that work efficiently and seamlessly between C++, Java, Python, PHP, Ruby, Erlang, Perl, Haskell, C#, Cocoa, JavaScript, Node.js, Smalltalk, OCaml
and Delphi and other languages.

##

https://thrift.apache.org/

https://thrift.apache.org/docs/install/
https://thrift.apache.org/docs/BuildingFromSource

http://grokbase.com/t/thrift/user/121t7jr1fv/c-library-requirements
https://stackoverflow.com/questions/32841565/how-to-enable-tnonblockingserver-while-im-building-thrift-0-9-2


##

    $ wget http://www-us.apache.org/dist/thrift/0.9.3/thrift-0.9.3.tar.gz
    $ tar xzf thrift-0.9.3.tar.gz
    $ cd thrift-0.9.3
    $ sudo apt-get install libboost-all-dev libevent-dev # for C++ library
    $ sudo apt-get install ant # for Java library
    $ ./configure --prefix=/usr/local/thrift/lib CXXFLAGS='-g -O2'
    $ make
    $ make check
    $ sudo make install

##

After the Thrift compiler is installed you will need to create a thrify file. This file is an interface definition made up of thrift types and Services.
The services you define in this file are implemented by the server and are called by any clients. The Thrift compiler is used to generate your Thrift File
into source code which is used by the different client libraries and the server you write. To generate the source from a thrift file run

    `$ thrift --gen <language> <Thrift filename>`



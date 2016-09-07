# Redis


##

https://redis.io/
https://redis.io/commands/
https://redis.io/clients/
https://redis.io/documentatioin/
https://redis.io/community/
https://redis.io/download/


##

The suggested way of installing Redis is compiling it from sources as Redis has no dependencies other than a working GCC compiler and libc.
Installing it using the package manager of your Linux distribution is somewhat discouraged as usually the available version is not the latest.
You can either download the latest Redis tar ball from the [redis.io](http://reids.io/) web site, or you can alternatively use this special URL that always points to the latest stable Redis version, that is, http://download.redis.io/redis-stable.tar.gz.

In order to compile Redis follow this simple steps:

    $ wget http://download.redis.io/redis-stable.tar.gz
    $ tar xzf redis-stable.tar.gz
    $ cd redis-stable
    $ make
    $ sudo make install

At this point you can try if your build works correctly by typing `make test`, but this is an optional step. After the compilation the `src` directory inside the Redis distribution is populated with the different executables that are part of Redis:

__redis-server__ is the Redis Server itself.
__redis-sentinel__ is the Redis Sentinel executable(monitoring and failover).
__redis-cli__ is the command line interface utility to talk with Redis.
__redis-benchmark__ is used to check Redis performances.
__redis-check-aof__ and __redis-check-dump__ are useful in the rate event of corrupted data files.

It is a good idea to copy both the Redis server and the command line interface in proper places, either manually using the following commands:

    $ sudo cp src/redis-server /usr/local/bin
    $ sudo cp src/redis-cli /usr/local/bin

Or just using:

    $ sudo make install

##

The simplest way to start the Redis server is just executing the redis-server binary without any argument.

    $ redis-server
    $ ...



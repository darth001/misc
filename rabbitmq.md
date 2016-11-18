# RabbitMQ


##

[RabbitMQ - Messaging that just works](https://www.rabbitmq.com/)
[RabbitMQ download page](https://www.rabbitmq.com/download.html)
[Installing on RPM-based Linux(CentOS, Fedora, OpenSUSE, RedHat)](https://www.rabbitmq.com/install-rpm.html)

##

* 1. Install Erlang(via repository from Erlang Solutions)

```
    $ sudo rpm -ivh https://packages.erlang-solutions.com/erlang-solutions-1.0-1.noarch.rpm
or
    $ sudo rpm --import https://packages.erlang-solutions.com/rpm/erlang_solutions.asc
    $ sudo tee /etc/yum.repos.d/erlang.repo <<EOF
[erlang-solutions]
name=Fedora $releasever - $basearch - Erlang Solutions
baseurl=https://packages.erlang-solutions.com/rpm/centos/$releasever/$basearch
gpgkey=https://packages.erlang-solutions.com/rpm/erlang_solutions.asc
gpgcheck=1
enabled=1
EOF

    $ sudo dnf install erlang erlang-doc erlang-manpages
```

* 2. Install RabbitMQ

```
    $ sudo rpm --import https::/www.rabbitmq.com/rabbitmq-release-signing-key.asc
    $ sudo rpm -ivh https://www.rabbitmq.com/releases/rabbitmq-server/v3.6.3/rabbitmq-server-3.6.3-1.noarch.rpm
or
    $ sudo rpm -ivh https://github.com/rabbitmq/rabbitmq-server/releases/download/rabbitmq_v3_6_3/rabbitmq-server-3.6.3-1.noarch.rpm
```

* 3. Run RabbitMQ

```
    $ sudo chkconfig rabbitmq-server on
    $ sudo service rabbitmq-server start
    $ sudo systemctl status rabbitmq-server.service
```

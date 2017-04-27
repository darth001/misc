#

##

https://www.mongodb.com/
https://docs.mongodb.com/
https://docs.mongodb.com/manual/tutorial/install-mongodb-on-red-hat/


Configure the package management system(yum)

    $ sudo tee /etc/yum.repos.d/mongodb-org-3.2.repo <<EOF
[mongodb-org-3.2]
name=MongoDB Repository
baseurl=https://repo.mongodb.org/yum/redhat/$releasever/mongodb-org/3.2/x86_64/
gpgcheck=1
enabled=1
gpgkey=https://www.mongodb.org/static/pgp/server-3.2.asc
EOF

Install the MongoDB packages and associated tools

    $ sudo dnf install mongodb-org

Run MongoDB Community Edition

- configure SELinux

* If SELinux is in `enforcing` mode, enable access to the relevant ports that MongoDB will use(default to 27017)

    semanage port -a -t mongd_port_t -p tcp 27017

* Disable SELinux by setting the `SELINUX` setting to `disabled` in `/etc/selinux/config`

    SELINUX=disabled

NOTE: reboot required for the changes to take effect.

* Set SELinux to `permissive` mode in `/etc/selinux/config` by setting the `SELINUX` setting to `permissive`

    SELINUX=permissive

NOTE: reboot required for the changes to take effect.

Also, you can instead use `setenfore` to change to `permissive` mode. `setenforce` does not require a reboot but is not persistent.

Alternatively, you can choose not to install the SELinux packages when you are installing your Linux operating system, or choose to remove the relevant packages. This option is the most invasive and is not recommended.


Start MongoDB

    sudo service mongod start

You can optionally ensure that MongoDB will start following a system reboot by issuing the following command:

    sudo chkconfig mongod on

Check MongoDB staus

    sudo service mongod staus

Stop MongoDB

    sudo service mongod stop

Restart MongoDB

    sudo service mongod restart

NOTE: For RHEL/CentOS 7 and recent Fedora, SysV is replace with systemd, so `systemctl` can be used.


##

ISSUES

## ERROR: Cannot write pid file to /var/run/mongodb/mongod.pid: No such file or directory

Add `mongodb.conf` to /lib/tmpfiles.d with following content:

    d /var/run/mongodb 0755 mongod mongod

## journal(/var/lib/mongo/journal) size too large

    $ sudo systemctl stop mongod.service
    $ sudo rm -rf /var/lib/mongo/journal
    $ echo 'smallfiles=true' >> /etc/mongod.conf
    $ sudo systemctl start mongod.service

## Cannot restart MongoDB

Remove lock file

    sudo rm /var/lib/mongo/mongod.lock



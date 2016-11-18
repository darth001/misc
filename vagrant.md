#


##

https://www.vagrantup.com/
https://www.vagrantup.com/downloads.html

https://atlas.hashicorp.com/boxes/search

https://atlas.hashicorp.com/centos/


##

* Download and install Vagrant

Get the latest version Vagrant from https://www.vagrantup.com/downloads.html and install it:

    $ wget https://releases.hashicorp.com/vagrant/1.8.6/vagrant_1.8.6_x86_64.rpm
    $ sudo rpm -ivh vagrant_1.8.6_x86_64.rpm

* Install a box(VirtualBox)

Search and install your target box from https://atlas.hashicorp.com/boxes/search

    $ mkdir -p vagrant/centos6
    $ cd vagrant/centos6
    $ vagrant init centos/6
    $ vagrant up

You can do these for centos/6, centos/7, debian/jessie64, debian/wheezy64, ubuntu/xenial64, ubuntu/trusty64, and so on.

NOTE: Often it will spend a lot of time to finish downloading the box, especially in China, so you can download the corresponding box directly from the official website.

    $ wget http://cloud.centos.org/centos/6/vagrant/x86_64/images/CentOS-6-x86_64-Vagrant-1609_01.VirtualBox.box
    $ vagrant box add --name centos6 CentOS-6-x86_64-Vagrant-1609_01.VirtualBox.box
    $ vagrant init
    $ vim Vagranfile

Now modify the parameter `config.vm.box` to the one you specify above, e.g., centos6,

    $ vagrant up

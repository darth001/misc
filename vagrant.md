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


##

Configure NFS

To sync folder between host and guest machines, NFS/rsync/SMB/VirtualBox shared folders are provided.
For Vagrant VirtualBox provider + CentOS, rsync is the default sync type while VirtualBox Guest Additions are not preinstalled, NFS is recommended, details at

https://seven.centos.org/2016/08/updated-centos-vagrant-images-available-v1607-01/

Given that both host and guest has NFS installed(NFS server required for host, NFS client required for guest), if VirtualBox provider used, you also make sure a private network setup,
this is due to a limitations of VirtualBox's built-in networking, VMware not affected(https://www.vagrantup.com/docs/synced-folders/nfs.html).
Related config are as follows,

    config.vm.network "private_network", ip: "192.168.2.2"
    config.vm.synced_folder ".", "/data", type: "nfs"

NOTE:

1. private_network should be enabled, orelse
`NFS requires a host-only network to be created.
Please add a host-only network to the machine (with either DHCP or a
static IP) for NFS to work.`

2. private_network type can be DHCP or Static IP, however, when dhcp type choosed, some error occurs:
`No guest IP was given to the Vagrant core NFS helper. This is an
internal error that should be reported as a bug.`

3. When using static IP, make sure not conflict with other network, such as your host's LAN network.

4. ake sure FIREWALL & SELinux rules permit NFS traffic.

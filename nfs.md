#


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
`
NFS requires a host-only network to be created.
Please add a host-only network to the machine (with either DHCP or a
static IP) for NFS to work.
`

2. private_network type can be DHCP or Static IP, however, when dhcp type choosed, some error occurs:
`
No guest IP was given to the Vagrant core NFS helper. This is an
internal error that should be reported as a bug.
`

3. When using static IP, make sure not conflict with other network, such as your host's LAN network.
`
The specified host network collides with a non-hostonly network!
This will cause your specified IP to be inaccessible. Please change
the IP or name of your host only network so that it no longer matches that of
a bridged or non-hostonly network.
`

4. ake sure FIREWALL & SELinux rules permit NFS traffic.
`
The following SSH command responded with a non-zero exit status.
Vagrant assumes that this means the command failed!

set -e
mkdir -p /software
mount -o vers=3,udp 192.168.2.1:/home/michael/vagrant/centos6-python2.7 /software
if command -v /sbin/init && /sbin/init --version | grep upstart; then
  /sbin/initctl emit --no-wait vagrant-mounted MOUNTPOINT=/software
fi


Stdout from the command:



Stderr from the command:

mount.nfs: Connection timed out
`

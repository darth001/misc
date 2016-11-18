# Linux Cluster


## Install RHEL/CentOS 7.0 on Multiple Servers using FTP Network Source


### Requirements

Server side:

CentOS minimal installation with vsftpd server and the binary DVD ISO image located on DVD/USB drive.

Client side:

Download CentOS 7 minimal ISO image.

### Installation

* Prepare Network Sources on server side
```
    # dnf install vsftpd
    # systemctl start vsftpd
    # ip addr show
or
    # ifconfig
    # firewall-cmd --permanent --add-service=ftp
    # systemctl restart firewalld.service
    # mount -o loop,ro /dev/sr0 /var/ftp/pub/
```

* Add Network Installation Sources to remote clients

Now it's time to install RHEL/CentOS 7 on other machines using as a FTP Source Installation the above configured server.
On the system that you will perform the installation of RHEL/CentOS 7 put the minimal bootable binary ISO image on DVD-ROM/USB
drive, for creating bootable USB drive, use Unetbootin Bootable tool.

After you have configured your Date and Time, Keyboard and Language, move Network and Hostname and switch your system Ethernet card to ON
to automatically obtain network configurations and gain network connectivity if you have a DHCP server on your network or configure it with
a static IP Address.

After the Network Card is active and operational it's time to add the Network Installation Sources.
Go to Software -> Installation Source from Installation Summary menu. Choose Network Installation Sources using FTP protocol and add your sources
configured earlier with the FTP server IP Address and path.

After you added the Network Installation Sources, hit on above Done button to apply changes and wait for the installer to detect and automatically
configure your Network Sources. After everything is configured you can move forward with the installation procedure 

##

http://www.ibm.com/developernetworks/systems/library/es-linuxclusterintro/index.html

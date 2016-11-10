#


##

https://www.digitalocean.com/community/tutorials/how-to-set-up-an-nfs-mount-on-ubuntu-16-04

NFS, or Network File System, is a distributed file system protocol that allows you to mound remote directories on your server.
This lets you manage storage space in a different location and write to that space from multiple clients. NFS provides a relatively
quick and easy way to access remote systems over a network and works well in situations where the shared resources will be accessed regularly.

* Install necessary components

On the Host,

    $ sudo apt-get update
    $ sudo apt-get install nfs-kernel-server

On the Client,

    $ sudo apt-get update
    $ sudo apt-get install nfs-common

* Create share directories on the host

Superusers can do anything anywhere on their system. However, NFS-mounted directories are not part of the system on which they are mounted,
so by default, the NFS server refuses to perform operations that require superuser privileges. This default restriction means that superusers
on the client cannot write files as root, re-assign ownership, or perform any other superuser tasks on the NFS mount.

Sometimes, however, there are trusted users on the client system who need to be able to do these things on the mounted file system but who have
no need for superuse access on the host. The NFS server can be configured to allow this, although it introduces an element of risk, as such a user
could gain root access to the entire system.

First we'll create a general-purpose NFS mount that uses default NFS behavior to make it difficult for a user with root privileges on the client
machine to interact with the host using those client superuser privileges. You might use something like this to store the files uploaded using a
content management system or to create space for users to easily share project files.

    $ sudo mkdir -p /var/nfs/general

NFS will translate any root operations on the client to the nobody:nogroup credentials as a security measure. Therefore, we need to change the directory
ownership to match those credentials.

    $ sudo chown nobody:nogroup /var/nfs/general

Second we want to make user home directories stored on the host available on client servers, while allowing trusted administrators of those client
servers the access they need to conveniently manage users.

* Configure the NFS exports on the host server

Now we'll dive into the NFS configuration file to set up the sharing of these resources.

    $ sudo vim /etc/exports

_BEGIN: /etc/exports
# directory_to_share    client(share_option1,...,share_optionN)
/var/nfs/general    192.168.1.101(rw,sync,no_subtree_check)
/home               192.168.1.101(rw,sync,no_root_squash,no_subtree_check)
END_

These options mean
__rw__: This option gives the client computer both read and write access to the volum
__sync__: This option forces NFS to write changes to disk before replying. This results in a more stable and consistent environment since the reply reflects the actual state of the remote volume. However, it also reduces the speed of file operations.
__no_subtree_check__: This option prevents subtree checking, which is a process where the host must check whether the file is actually still available in the exported tree for every request. This can cause many problems when a file is renamed while the client has it opened. In almost all cases, it is better to disable subtree checking.
__no_root_squash__: By default, NFS translates requests from a root user remotely into a non-privileged user on the server. This was intended as security feature to prevent a root account on the client from using the file system of the host as root. no_root_squash disables this behavior for certain shares.

    $ sudo systemctl restart nfs-kernel-server

* Adjust Firewall on the host

Check the firewall status to see if it's enabled and if so, to see what's currently permitted:

    $ sudo ufw status

With many applications, you can use `sudo ufw app list` and enable them by name `sudo ufw allow OpenSSH`, but nfs is not one of those. Because ufw also checks
/etc/services for the port and protocol of a service, we can still add NFS by name. Best practice recommends that you enable the most restrictive rule that will still
allow the traffic you want to permit, so rather than enabling traffic from just anywhere, we can be specific.

Use the following command to open port 2049 on the host,

    $ sudo ufw allow from 192.168.1.101 to any port nfs

and verify the change by typing

    $ sudo ufw status

* Create the mount points on the client

In order to make the remote shares available on the client, we need to mount the host directory on an empty client directory.

Note: If there are files and directories in your mount point, as soon as you mount the NFS share, they'll be hidden. Be sure if you mount in a directory that already exists that the directory is empty.

    $ sudo mkdir -p /nfs/general
    $ sudo mkdir -p /nfs/home

* Mounte the directories on the client

Mount the shares by addressing the host server,

    $ sudo mount 192.168.1.100:/var/nfs/general /nfs/general
    $ sudo mount 192.168.1.100:/home /nfs/home

Check the mount with df,

    $ df -hT

* Mount the remote NFS directories at boot

We can mount the remote NFS shares automatically at boot by adding them to /etc/fstab file on the client.

    $ sudo vim /etc/fstab

_BEGIN, /etc/fstab
192.168.1.100:/var/nfs/general  /nfs/general    nfs auto,nofail,noatime,nolock,intr,tcp,actimeo=1800    0   0
192.168.1.100:/home             /nfs/home       nfs auto,nofail,noatime,nolock,intr,tcp,actimeo=1800    0   0
-_

* Unmount NFS remote share

If you no longer want the remote directory to be mounted on your system, you can unmount it by moving out of the share's directory structure and unmounting, like this:

    $ cd ~
    $ sudo umount /nfs/home
    $ sudo umount /nfs/general

If you want to prevent them from being remounted on the next reboot, edit /etc/fstab and either delete the line or comment it out by placing a # symbol at the beginning of the line.
You can also prevent auto-mounting by removing the auto option, which will allow you to mount it manually.

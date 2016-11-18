# Linux Knowledge Base


## [DISK]No space left on device while there is plenty of space available

__Synopsis__
During an operation that writes to the disk, the operation fails with the error message No space left on device. However, after validating this with the df command plenty of space is still available.

__Analysis__
When space is concerned, there are two important factors that a system has to consider:
* The first one is the most obvious: there are must be space available on the file system, meaning that there are still unused data blocks available on the file system.
* However, an often overlooked second factor is that must still be metadata blocks available on the file system as well. In most file systems, these are called i-nodes or inodes. Whenever a file is created on a file system, an inode is used to contain information about the file. But many file systems have a fixed amount of these inodes(which is set during the mkfs operation of the file system).

To check the state of the inodes on a Linux system, use `df -i`.

__Resolution__
Verify the system has free inodes available with command `df -i /`.
If indeed short on inodes, try removing obsolete or unnecessary files on the file system. There is, sadly enough, no way to increase the number of inodes on a file system once the file system has been created.

## [SSH]ssh -t user@remote sudo yum install httpd
## [SSH]expect

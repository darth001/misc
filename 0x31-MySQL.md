# MySQL Installation


## Replacing a Third-Party Distribution of MySQL Using the MySQL Yum Repository

For Fedora 24, we can replace the third-party distribution of MySQL with the latest GA release(from the MySQL 5.7 series currently)
from the MySQL Yum repository.

### Replacing a Native Third-Party Distribution of MySQL

If you have installed a third-party distribution of MySQL from a native software repository(that is, a software repository provided by your own Linux distribution), follow these steps:

* 1. Backing Up Your Database
To avoid loss of data, always back up your database before trying to replace your MySQL installation using the MySQL Yum repository. See [Chapter 8, Backup and Recovery](https://dev.mysql.com/doc/refman/5.7/en/backup-and-recovery.html), on how to backup your database.
* 2. Adding the MySQL Yum Repository
Adding the MySQL Yum repository to your system's repository list by following the instructions given in [Adding the MySQL Yum Repository](https://dev.mysql.com/doc/refman/5.7/en/linux-installation-yum-repo.html#yum-repo-setup).
* 3. Replacing the Native Third-Party Distribution by a Yum update or DNF upgrade.
By design, the MySQL Yum repository will replace your native, third-party MySQL with the latest GA release(from the MySQL 5.7 series currently) from the MySQL Yum repository when you perform a yum update command(or dnf upgrade for dnf-enabled systems) on the system, or a yum update mysql-server(or dnf upgrade mysql-server for dnf-enabled systems).

### Replacing a Nonnative Third-Party Distribution of MySQL

If you have installed a third-party distribution of MySQL from a nonnative software repository(that is, a software repository not provided by your own Linux distribution), follow these steps:

* 1. Backing Up Your Database
To avoid loss of data, always back up your database before trying to replace your MySQL installation using the MySQL Yum repository.
* 2. Stopping Yum from Receiving MySQL Packages from Third-Party, Nonnative Repositories
Before you can use the MySQL Yum repository for installing MySQL, you must stop your systems from receiving MySQL packages from any third-party, nonnative Yum repositories.
For example, if you have installed MariaDB using their own software repository, get a list of installed MariaDB packages using the following command(for dnf-enabled systems, replace yum in the command with dnf):

    $ yum list installed mariadb\*

From the command output, we can identify the installed packages(MariaDB-common, MariaDB-compat, and MariaDB-server) and the source of them(a nonnative software repository named mariadb).

As another example, if you have installed Percona using their own software repository, get a list of the installed Percona packages using the following command(for dnf-enabled systems, replace yum in the command with dnf):

    $ yum list installed Percona\*

From the command output, we can identify the installed packages(Percona-Server-client, Percona-Server-server, Percona-Server-shared, and percona-release.noarch) and the source of them(a nonnative software repository named percona-release).

If you are not sure which third-party MySQL fork you have installed, this command should reveal it and list the RPM packages installed for it, as well as the third-party repository that supplies the packages(for dnf-enabled systems, replace yum in the command with dnf):

    $ yum --disablerepo=\*provides mysql\*

The next step is to stop Yum from receiving packages from the nonnative repository. If the yum-config-manager utility is supported on your platform, you can, for example, use this command for stopping delivery from MariaDB(on dnf-enabled systems, use the dnf-config-manager command instead of yum-config-manager):

    $ sudo yum-config-manager --disable mariadb

Use this command for stopping delivery from Percona(on dnf-enabled systems, use the dnf-config-manager command instead of yum-config-manager):

    $ sudo yum-config-manager --disable percona-release

You can perform the same task by removing the entry for the software repository existing in one of the repository files under the /etc/yum.repos.d/ directory. This is how the entry typically looks for MariaDB:

[mariadb]
name=MariaDB
baseurl=<base url for repository>
gpgkey=<url for GPG key>
gpgcheck=1

This entry is usually found in the file /etc/yum.repos.d/MariaDB.repo for MariaDB--delete the file, or remove entry from it(or from the file in which you find the entry).

* 3. Uninstalling the Nonnative Third-Party MySQL Distribution of MySQL
The nonnative third-party MySQL distributioin must first be uninstalled before you can use the MySQL Yum repository to install MySQL. For the MariaDB packages found in Step 2 above, uninstall them with the following command(for dnf-enabled systems, replace yum in the command with dnf):

    $ sudo yum remove MariaDB-common MariaDB-compat MariaDB-server

For the Percona packages we found in Step 2 above(for dnf-enabled systems, replace yum in the command with dnf):

    $ sudo yum remove Percona-Server-client-55 Percona-Server-server-55 Percona-Server-shared-55.i686 percona-release

* 4. Installing MySQL with the MySQL Yum repository by following the instructions given in [Section 2.5.1, "Installing MySQL on Linux Using the MySQL Yum Repository"](https://dev.mysql.com/doc/refman/5.7/en/linux-installation-yum-repo.html).

## Installing MySQL on Linux Using the MySQL Yum Repository

[Installation Guide](https://dev.mysql.com/doc/refman/5.7/en/linux-installation-yum-repo.html)


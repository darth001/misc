# Service Management (Ubuntu 14.04)

There are services that can be enabled/disabled using the GUI (like the startup application) or the terminal.
For the Terminal you have several options. First, open a terminal (Type "terminal" in the dash, for example, and open it). Then:

## Enabling / Disabling a service

To toggle a service from starting or stopping permanently you would need to:

    $ echo manual | sudo tee /etc/init/SERVICE.override

where the stanza manual will stop Upstart from automatically loading the service on next boot. Any service with the .override ending will take precedence over the original service file. You will only be able to start the service manually afterwards. If you do not want this then simply delete the .override. For example:

    $ echo manual | sudo tee /etc/init/mysql.override

Will put the MySQL service into manual mode. If you do not want this, afterwards you can simply do

    $ sudo rm /etc/init/mysql.override

and Reboot for the service to start automatically again. Of course to enable a service, the most common way is by installing it. If you install Apache, Nginx, MySQL or others, they automatically start upon finishing installation and will start every time the computer boots. Disabling, as mentioned above, will make use of the service manual.

## Temporary enabling/disabling services

To stop and start services temporarily (Does not enable / disable them for future boots), you can type service SERVICE_NAME. For example:

    $ sudo service apache2 stop (Will STOP the Apache service until Reboot or until you start it again).
    $ sudo service apache2 start (Will START the Apache service assuming it was stopped before.).
    $ service apache2 status (Will tell you the STATUS of the service, if it is either enabled/running of disabled/NOT running.).
    $ sudo service apache2 restart (Will RESTART the service. This is most commonly used when you have changed, a config file. In this case, if you changed either a PHP configuration or an Apache configuration. Restart will save you from having to stop/start with 2 command lines)
    $ service apache2 (In this case, since you did not mention the ACTION to execute for the service, it will show you all options available for that specific service.) This aspect varies depending on the service, for example, with MySQL it would only mention that it is missing a parameter. For other services like networking service it would mention the small list of all options available.

## UPSTART

If we want to use the official Upstart way (Note that, for the moment, not all services have been converted to Upstart), we could use the following commands:

    $ status SERVICE - This will tell us if a converted service is running or not. Note that this is deprecated in favor of start, stop, status & restart. It will also tell us if a service has not yet been converted to upstart:

A converted service would typically output the current status (Starting, Running, Stopping...) and process ID. A non converted service would give an error about an unknown job.

Some shortcuts may only work with the service command above but not with the commands below unless they are 100% converted to upstart services:

START - sudo start mysql
STOP - sudo stop mysql
RESTART - sudo restart mysql
STATUS - sudo status smbd

## SYSTEMD

Starting with Ubuntu 15.04, Upstart will be deprecated in favor of Systemd. With Systemd to manage the services we can do the following:

    $ systemctl start SERVICE.service - Use it to start a service. Does not persist after reboot
    $ systemctl stop SERVICE.service - Use it to stop a service. Does not persist after reboot
    $ systemctl restart SERVICE.service - Use it to restart a service
    $ systemctl reload SERVICE.service - If the service supports it, it will reload the config files related to it without interrupting any process that is using the service.
    $ systemctl status SERVICE.service - Shows the status of a serviceTells whether a service is currently running.
    $ systemctl enable SERVICE.service - Turns the service on, on the next reboot or on the next start event. It persists after reboot.
    $ systemctl disable SERVICE.service - Turns the service off on the next reboot or on the next stop event. It persists after reboot.
    $ systemctl is-enabled SERVICE.service - Check if a service is currently configured to start or not on the next reboot.
    $ systemctl is-active SERVICE.service - Check if a service is currently active.
    $ systemctl show SERVICE.service - Show all the information about the service.

Currently there are actually three different ways for software to be started as a service in Ubuntu, SysV, Upstart and systemd. A service is defined here as a program run by the system in the background, as opposed to one started and run directly by the user.

## SysV

The traditional way to start services in Linux was to place a script in /etc/init.d, and then use the update-rc.d command (or in RedHat based distros, chkconfig) to enable or disable it.

This command uses some mildly complicated logic to create symlinks in /etc/rc#.d, that control the order of starting services. If you run ls /etc/rc2.d you can see the order that services will be killed with a file name like K##xxxx and started with file names S##xxxx. The ## in S##xxxx means a "start order" for service xxxx. Conversely, the ## in K##xxxx means the kill order for service xxxx.

One major issue with SysV was that when booting the system, everything had to be done in serial, one thing after another, making system boot times really slow. Attempts were made to parallelize this, but they were haphazard and hard to take full advantage of. This was the main reason that Upstart was created.

## Upstart

Upstart uses job definition files in /etc/init to define on what events a service should be started. So, while the system is booting, upstart processes various events, and then can start multiple services in parallel. This allows them to fully utilize the resources of the system, for instance, by starting a disk-bound service up while another CPU-bound service runs, or while the network is waiting for a dynamic IP address to be assigned.

You can see all of the upstart job files by running ls /etc/init/*.conf

Let me just stop here and say that if you don't know what a service is, or what it does, DO NOT disable it!

Not all services have been converted to upstart. While working on the server team at Canonical for the past few months, I've worked on a number of converted job files, and the nicest part is that it allows one to get rid of all the script "magic" and just put in a few commands here and there to define exactly how to start the service, and nothing more. But for now, only a handful of traditional network services, like squid and samba, have been converted.

Is a service upstart-based?

In order to figure out if a service is upstart-based, you can run the status command:

    $ status servicename

If it's an upstart job, it will show this:

    $ status statd
    statd start/running, process 942

But if it's not, you'll see something more like this:

    $ status apache2
    status: Unknown job: apache2

In this case, apache2 has not been converted to upstart. So, to disable apache2 you just run

    $ sudo update-rc.d apache2 disable
    $ sudo service apache2 stop

Disable services (jobs) in upstart

Upstart job definitions do not have an update-rc.d command. To disable the job, you need to edit the job file directly to disable it. There are two ways to do this.

If you want to still be able to manually start it, then you need to comment out the start on condition. Say you want to install samba, but not have it start automatically. Here is the job file (in natty):

    description "SMB/CIFS File Server"
    author      "Steve Langasek <steve.langasek@ubuntu.com>"
    
    start on local-filesystems
    stop on runlevel [!2345]
    
    respawn
    
    pre-start script
        RUN_MODE="daemons"

        [ -r /etc/default/samba ] && . /etc/default/samba

        [ "$RUN_MODE" = inetd ] && { stop; exit 0; }

        install -o root -g root -m 755 -d /var/run/samba
    end script

    exec smbd -F

To disable samba, you can just put a # in front of the "start on local-filesystems". Note that while it won't start back up on boot, you still need to stop it this time with

    $ sudo service smbd stop

If, however, you never want samba to start, I'd suggest actually removing the package. If, however, you want it installed, but not startable, you can also do:

    $ mv /etc/init/smbd.conf /etc/init/smbd.conf.disabled

Disable a service using start/stop stanza (as of 11.04)

Starting with the version of upstart that will be in 11.04, there is a new keyword that disables the start on and stop on stanzas: manual. So another way to disable the service as of 11.04 is to do:

    $ echo 'manual' | sudo tee /etc/init/mysql.override

    $ echo manual >> /etc/init/mysql.override # command from root shell

You can create an override file to disable a service without editing the job definition at all, by just putting the manual keyword in it.

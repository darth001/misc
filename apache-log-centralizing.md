#


##

Centralizing Apache Logs

Apache already logs by default so you can see the access log and error log on your local system. If you have many servers, you can
centralize all the logs to one place for storage and analysis. Often times this is either an internal log server or a cloud-based log service. Some people use rsync to this, some use some other proprietary software agent. We recommend allowing rsyslog to do the file monitoring and forwarding for you because it’s already installed on most Linux servers and it’s very reliable. Here are two methods you can use to centralize your logs using rsyslog or another daemon of your choice.


##

File Monitoring

Apache already creates local log files by default. File monitoring has the advantage of giving you a local backup of your logs. If you experience any problems with your network or your log management system, you’ll always be able to view the logs on your local server. One disadvantage is that you’ll have to manage those files by, for example, setting up a log rotation so they don’t fill up your disk. Luckily, distributions like Ubuntu already have log rotation set up. This might not be a good option if your server is limited by disk writes.

Here is an example configuration for rsyslog that will monitor your Apache log files. You’ll need to replace the file names with your own values.
```
$ModLoad imfile
$InputFilePollInterval 10 
$PrivDropToGroup adm
$WorkDirectory /var/spool/rsyslog

# Apache access file:
$InputFileName /var/log/apache2/access.log
$InputFileTag apache-access:
$InputFileStateFile stat-apache-access
$InputFileSeverity info
$InputFilePersistStateInterval 20000
$InputRunFileMonitor

#Apache Error file: 
$InputFileName /var/log/apache2/error.log
$InputFileTag apache-error:
$InputFileStateFile stat-apache-error
$InputFileSeverity error
$InputFilePersistStateInterval 20000
$InputRunFileMonitor
````

You should configure rsyslog to send to your chosen destination, then restart it so the changes take effect.

	$ sudo service rsyslog restart

Some log management vendors have scripts or agents that will monitor these log files, making setup easier. For example, Loggly built a script that will automatically configure rsyslog to monitor your Apache logs.


##

Pipe To Logger

Apache also allows you to setup custom loggers. The most popular example is to pipe to logger, which forwards these logs over a syslog socket to the syslog daemon. Sending your logs via syslog could have performance advantages if your server is limited by disk writes. Also, you don’t have to worry about managing files. On the downside, you won’t have a local backup. If rsyslog has a problem processing messages from the socket, it could use up all of the available space in the buffer and cause you to lose log messages. To do this, open your Apache configuration file and then incorporate the following:
```
ErrorLog  "|/usr/bin/tee -a /var/log/www/error.log  | /usr/bin/logger -thttpd -plocal6.err"
CustomLog "|/usr/bin/tee -a /var/log/www/access.log | /usr/bin/logger -thttpd -plocal6.notice" extended_ncsa
```

Once you’ve made the changes to the configuration file, you’ll need to restart the service.

	$ sudo service apache2 restart

Now your Apache logs should start flowing to your syslog daemon. You should configure your syslog daemon to send to your chosen destination.
Filtering Apache Logs

In some situations you may want to filter your logs before centralizing them in order to use less resources on the remote system. For example, you may want to send only error codes in order to reduce the volume of data you need to store. Here’s how we can filter out just the 500s and 502 codes. It works with rsyslog 7.x and lower.
```
if $msg contains ' 500 ' and $programname == 'apache2-access' then @@
if $msg contains ' 502 ' and $programname == 'apache2-access' then @@
```

Once you’ve made the changes to the configuration file, you’ll need to restart the service.

	$ sudo service rsyslog restart


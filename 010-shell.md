#


##

```
if ! rpm -qa | grep -qw ntp; then
    yum install ntp
fi
```



## Start ntpd if it's not already running.
```
if ps aux | grep -v grep | grep "[n]tpd" > /dev/null
then
    echo "ntpd is running." > /dev/null
else
    systemctl start ntpd.service > /dev/null
    echo "Started ntpd."
fi
systemctl enable ntpd.service
```

## Apache too many errors?

    $ cat access.log | cut -d' ' -f9 | sort | uniq -c | sort -nr

## Apache what is causing 404s?

    $ grep " 404 " access.log | cut -d' ' -f 7 | sort | uniq -c | sort -nr

## Aapache site loading too slow?

    $ cat access.log | cut -d' ' -f1 | sort | uniq -c | sort -nr

## Apache too much load from one site?

    $ cat access.log | cut -d' ' -f 1 | sort | uniq -c | sort -nr

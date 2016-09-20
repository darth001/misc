#


##

iptables

https://fedoraproject.org/wiki/How_to_edit_iptables_rules

Listing rules:

    $ sudo iptables -L
    $ sudo iptables -L -n
    $ sudo iptables -L -v

    $ sudo iptables -S

Appending rules:

    $ sudo iptables -A INPUT -m state --state NEW -m tcp -p tcp --dport 80 -J ACCEPT
    $ sudo iptables-save > iptables.backup

    $ netstat -tunlp | less # or ss -tunlp | less

##



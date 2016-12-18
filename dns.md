#


##

Configure BIND as a Private Network DNS Server


An important part of managing server configuration and infrastructure includes maintaining an easy way to
look up network interfaces and IP addresses by name, by setting up a proper Domain Name Server(DNS).
Using fully qualified domain names(FQDNs), instead of IP addresses, to specify network addresses eases the
configuration of services and applications, and increases the maintainability of configuration files. Setting
up your own DNS for your private network is a great way to improve the management of your servers.


* Install BIND on DNS servers

On both DNS servers, install BIND with yum:

    $ sudo yum install bind bind-utils

* Configure Primary DNS Server

BIND's configuration consists of multiple files, which are included from the main configuration file, `named.conf`.
These filenames begin with "named" because that is the name of the process that BIND runs.

Configure BIND

BIND's process is known as `named`. As such, many of the files refer to "named" instead of "BIND".
On _ns1_, open the `named.conf` file for editing:

    $ sudo vim /etc/named.conf

Above the existing `options` block, create a new ACL block called `trusted`. This is where we will define list of
clients that we will allow recursive DNS queries from(i.e. your servers that are in the same datacenter as ns1).

```
acl "trusted" {
    10.0.10.11;   # ns1 - can be set to localhost
    10.0.20.12;   # ns2
    10.0.100.101; # host1
    10.0.100.102; # host2
};
```

Now that we have our list of trusted DNS clients, we will want to edit the `options` block.
Add the private IP address of ns1 to the `listen-on port 53` directive, and comment out the `listen-on-v6` line:

```
options {
    listen-on port 53 {127.0.0.1; 10.0.10.11;};
    #listen-on-v6 port 53 {::1;};
```

Below those entries, change the `allow-transfer` directive to from "none" to ns2's private IP address. Also, change
`allow-query` directive from "localhost" to "trusted":
```
options {
    allow-transfer {10.0.20.12;}; # disable zone transfers by default
    allow-query {trusted;}; # allows queries from "trusted" clients
```

At the end of the file, add the following line:
```
include "/etc/named/named.conf.local";
```

Now save and exit named.conf. The above configuration specifies that only your own servers(the "trusted" ones) will be able to query your DNS servers.


* Configure Local File

Configure the local file to specify DNS zones.

On ns1, open the named.conf.local file for editing:

    $ sudo vim /etc/named/named.conf.local

This file should be empty. Here, we will specify our forward and reverse zones.

Add the forward zone:
```
zone "dc-nj.digitech.com" {
    type master;
    file "/etc/named/zones/db.dc-nj.digitech.com"; // zone file path
};
```

Assuming that our private subnet is 10.0.0.0/16, add the reverse zone:
```
zone "0.10.in-addr.arpa" {
    type master;
    file "/etc/named/zones/db.10.0"; # 10.0.0.0/16 subnet
};
```
If your servers span multiple private subnets but are in the same datacenter, be sure to specify an additional zone and zone file for each distinct subnet.

* Create Forward Zone File

The forward zone file is where we define DNS records for forward DNS lookups.
That is, when the DNS receives a name query, "host1.dc-nj.digitech.com" for example, it will look in the forward zone file to resolve host1's corresponding private IP address.

    $ sudo vim /etc/named/zones/db.dc-nj.digitech.com

First, you will want to add the SOA record.

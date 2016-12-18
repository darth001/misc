#


##

Domain Terminology


Domain Name System

The domain name system, more commonly known as "DNS" is the networking system in place that allows us to
resolve human-friendly names to unique addresses.

Domain Name

A domain name is the human-friendly name that we are used to associating with an internet resource.

IP Address

An IP address is what we call a network addressable location. Each IP address must be unique within its network.
IPv4, the most common form of addresses, are writen as four sets of numbers, each set of having up to three digits,
with each set separated by a dot. With DNS, we map a name to that address so that you do not have to remember a
complicated set of numbers for each place you wish to visit on a network.

Top-Level Domain

A top-level domain, or TLD, is the most general part of the domain. The top-level domain is the furthest portion
to the right(as separated by a dot). Common top-level domains are "com", "net", "org", "gov", "edu", and "io".

Top-level domains are at the top of the hierarchy in terms of domain names. Certain parties are given management
control over top-level domains by ICANN(Internet Corporation for Assigned Names and Numbers). These parties can then
distribute domain names under the TLD, usually through a domain registrar.

Hosts

Within a domain, the domain owner can define individual hosts, which refer to separate computers or services accessible
through a domain. For instance, most domain owners make their web servers accessible through the bare domain(example.com)
and also through the "host" definition "www"(www.example.com).

You can have other host definitions under the general domain. You could have API access through an "api" host(api.example.com)
or you could have ftp access by defining a host called "ftp" or "files"(ftp.example.com or files.example.com). The host names
can be arbitrary as long as they are unique for the domain.

Subdomains

A subject related to hosts are subdomains.
DNS works in a hierarchy. TLD can have many domains under them. For instance, the "com" TLD has both "google.com" and "ubuntu.com" underneath it.
A "subdomain" refers to any domain that is part of a larger domain. In this case, "ubuntu.com" can be said to be a subdomain of "com". This is typically
just called the domain or the "ubuntu" portion is called a SLD, which means second level domain. Likewise, each domain can control "subdomains"
that are located under it. This is usually what we mean by subdomains. For instance you could have a subdomain for the history department of your school at
"www.history.school.edu". The "history" portion is a subdomain.

The difference between a host name and a subdomain is that a host defines a computer or resource, while a subdomain extends the parent domain.
It is a method of subdividing the domain itself.

Fully Qualified Domain Name

A fully qualified doamin name, often called FQDN, is what we call an absolute domain name. Domains in the DNS system can be given relative to one another,
and as such, can be somewhat ambiguous. A FQDN is an absolute name that specifies its location in relation to the absolute root of the domain name system.

This means that it specifies each parent domain including the TLD. A proper FQDN ends with a dot, indicating the root of the DNS hierarchy.

Name Server

A name server is a computer designated to translate domain names into IP addresses. These servers do most of the work in the DNS system,
Since the total number of domain translations is too much for any one server, each server may redirect request to other name servers or delegate
responsibility for a subset of subdomains they are responsible for.

Name servers can be "authoritative", meaning that they give answers to queries about domains under their control. Otherwise, they may point to other
servers, or serve cached copies of other name servers' data.

Zone File

A zone file is a simple text file that contains the mappings between domain names and IP addresses. This is how the DNS system finally finds out which IP
addresses should be contacted when a user requests a certain domain name.

Zone files reside in name servers and generally define the resources available under a specific domain, or the place that one can go to get that information.

Records

Within a zone file, records are kept. In its simplest form, a record is basically a single mapping between a resource and a name. These can map a domain name
to an IP address, define the name servers for the domain, define the mail servers for the domain, etc.
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

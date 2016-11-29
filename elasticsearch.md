# elasticsearch


##

https://elastic.co/
https://www.elastic.co/downloads/elasticsearch

```
    $ sudo tee /etc/yum.repos.d/elasticsearch.repo <<EOF
[elasticsearch-2.x]
name=Elasticsearch repository for 2.x packages
baseurl=https://packages.elastic.co/elasticsearch/2.x/centos
gpgcheck=1
gpgkey=https://packages.elastic.co/GPG-KEY-elasticsearch
enabled=1
EOF

    $ sudo dnf install elasticsearch
    $ sudo systemctl enable elasticsearch
    $ sudo systemctl start elasticsearch
```

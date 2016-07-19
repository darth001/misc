# Ubuntu Install HOWTO

## Repository update

    $ sudo apt-get update

## Some tools

    $ sudo apt-get install gnome-tweak-tool unity-tweak-tool

## Some fonts

    $ sudo apt-get install fonts-droid fonts-roboto fonts-wqy-microhei

### No LSB modules are available.

    $ sudo apt-get install lsb-core

## Check Ubuntu arch

    $ file /sbin/init
    $ uname -a

## Check available package information

    $ apt-cache policy <package-name>

## GPG Error
`GPG error: https://apt.dockerproject.org ubuntu-trusty InRelease: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY F76221572C52609D`

    $ sudo apt-key adv --keyserver keyserver.ubuntu.com --recv-keys F76221572C52609D
    $ sudo apt-get update

### SNIMissingWarning, InsecurePlatformWarning
```
michael@michael-B85M-D3H:~/python $ sudo pip install --upgrade requests
[sudo] password for michael: 
The directory '/home/michael/.cache/pip/http' or its parent directory is not owned by the current user and the cache has been disabled. Please check the permissions and owner of that directory. If executing pip with sudo, you may want sudo's -H flag.
The directory '/home/michael/.cache/pip' or its parent directory is not owned by the current user and caching wheels has been disabled. check the permissions and owner of that directory. If executing pip with sudo, you may want sudo's -H flag.
/usr/local/lib/python2.7/dist-packages/pip/_vendor/requests/packages/urllib3/util/ssl_.py:318: SNIMissingWarning: An HTTPS request has been made, but the SNI (Subject Name Indication) extension to TLS is not available on this platform. This may cause the server to present an incorrect TLS certificate, which can cause validation failures. You can upgrade to a newer version of Python to solve this. For more information, see https://urllib3.readthedocs.org/en/latest/security.html#snimissingwarning.
  SNIMissingWarning
  /usr/local/lib/python2.7/dist-packages/pip/_vendor/requests/packages/urllib3/util/ssl_.py:122: InsecurePlatformWarning: A true SSLContext object is not available. This prevents urllib3 from configuring SSL appropriately and may cause certain SSL connections to fail. You can upgrade to a newer version of Python to solve this. For more information, see https://urllib3.readthedocs.org/en/latest/security.html#insecureplatformwarning.
    InsecurePlatformWarning
```

    $ sudo pip install --upgrade urllib3
    $ sudo pip install urllib3[secure]

## Wireshark

    $ sudo apt-get install wireshark
    $ sudo dpkg-reconfigure wireshark-common
    $ sudo usermod -a -G wireshark michael

## Install Python packages

    $ sudo apt-get update
    $ sudo apt-get install python-dev libfreetype6-dev
    $ sudo pip install numpy scipy matploylib pandas

## R
    
    $ echo "deb https://mirrors.tuna.tsinghua.edu.cn/CRAN/bin/linux/ubuntu trusty/" | sudo tee -a /etc/apt/sources.list.d/r-lang.list
    $ sudo apt-get update
    $ sudo apt-get install r-base

## Jenkins

    $ echo "deb http://pkg.jenkins-ci.org/debian binary/" | sudo tee -a /etc/apt/sources.list.d/jenkins.list
    $ sudo apt-get update
    $ sudo apt-get install jenkins

## ElasticSearch

    $ wget -O- https://packages.elastic.co/GPG-KEY-elasticsearch | sudo apt-key add -
    $ echo "deb https://packages.elastic.co/elasticsearch/2.x/debian stable main" | sudo tee -a /etc/apt/sources.list.d/elasticsearch-2.x.list
    $ sudo apt-get update
    $ sudo apt-get install elasticsearch

## SlatStack

    $ wget -O- https://repo.slatstack.com/apt/ubuntu/14.04/amd64/latest/SLATSTACK-GPG-KEY.pub | sudo apt-key add -
    $ echo "deb http://repo.slatstack.com/apt/ubuntu/14.04/amd64/latest trusty main" | sudo tee -a /etc/apt/sources.list.d/slatstack.list
    $ sudo apt-get update
    $ sudo apt-get install salt-master salt-minion salt-ssh salt-syndic salt-cloud salt-api

##

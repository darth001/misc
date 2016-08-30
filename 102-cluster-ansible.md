#


##

http://docs.ansible.com/
http://docs.ansible.com/ansible/intro_installation.html

Running from source:
```
    $ git clone git://github.com/ansible/ansible.git --recursive
    $ cd ansible
    $ sudo easy_install pip
    $ sudo pip install paramiko PyYAML Jinja2 httplib2 six
    $ source hacking/env-setup
```
NOTE for updates:
```
    $ git pull --rebase
    $ git submodule update --init --recursive
```

From yum(or dnf):
```
    # install the  epel-release RPM if needed on CentOS, RHEL, or Scientific Linux
    $ sudo yum install ansible
```

From apt:
```
    $ sudo apt-get install software-properties-common
    $ sudo apt-add-repository ppa:ansible/ansible
    $ sudo apt-get update
    $ sudo apt-get install ansible
```

From pip(RECOMMENDED):
```
    $ sudo easy_install pip
    $ sudo pip install ansible
```

##

http://os.51cto.com/art/201503/467553.htm

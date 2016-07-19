# Fedora 24 Setup

## Add youself to group wheel, assume michael
    $ su -
    # gpasswd -a michael wheel
    # lid michael

## Install some tools
    $ sudo dnf -y update
    $ sudo dnf -y group install with-optional 'Development Tools'
    $ sudo dnf -y group install with-optional 'C Development Tools and Libraries'
    $ sudo dnf -y install gnome-tweak-tool lynx w3m

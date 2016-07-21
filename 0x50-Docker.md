# Docker for Fedora 23

##

[Docker for Fedora 23](https://docs.docker.com/engine/installatioin/linux/fedora/)

    $ sudo dnf update
    $ sudo cat > /etc/yum.repos.d/docker.repo

```
[dockerrepo]
name=Dcoker Repository
baseurl=https://yum.dockerproject.org/repo/main/fedora/$releasever/
enabled=1
gpgcheck=1
gpgkey=https://yum.dockerproject.org/gpg
```

    $ sudo dnf install docker-engine
    $ sudo systemctl enable docker
    $ sudo systemctl start docker
    $ sudo docker run hello-world

##

* Show the Docker version information

    `$ sudo docker version`

* Display system-wide information

    `$ sudo docker info`

* Pull an image or a repository from a registery

    `$ sudo docker pull <image-or-repo-name>`

* Run a command in a new container

    `$ sudo docker run <command>`

* List images

    `$ sudo docker images`

* List containers

    `$ sudo docker ps`

* Remove one or more containers

    `$ sudo docker rm <container-name>`

* Remove one or more images

    `$ sudo docker rmi <image-name>`

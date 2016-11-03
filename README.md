# docker-ubuntu-32bit - Docker base images for 32bit Ubuntu

# ABOUT

docker-ubuntu-32bit is a collection of [debootstrap](https://wiki.debian.org/Debootstrap)-generated 32-bit Ubuntu base images.

# DOCKER HUB

https://registry.hub.docker.com/u/mcandre/docker-ubuntu-32bit/

# EXAMPLE

```
$ make
docker run --rm --privileged -v $(pwd):/mnt -t ubuntu:15.04 sh -c 'apt-get update && apt-get install -y debootstrap && mkdir /chroot && debootstrap --arch i386 vivid /chroot && cd /chroot && tar czvf /mnt/rootfs.tar.gz .'
...

docker build -t mcandre/docker-ubuntu-32bit:latest .
Step 0 : FROM scratch
Step 1 : MAINTAINER Andrew Pennebaker <andrew.pennebaker@gmail.com>
Step 2 : ADD rootfs.tar.gz /
Successfully built babc33fdd1bd

docker run --rm mcandre/docker-ubuntu-32bit:latest sh -c 'cat /etc/*release*'
DISTRIB_ID=Ubuntu
DISTRIB_RELEASE=15.04
DISTRIB_CODENAME=vivid
DISTRIB_DESCRIPTION="Ubuntu 15.04"
NAME="Ubuntu"
VERSION="15.04 (Vivid Vervet)"
ID=ubuntu
ID_LIKE=debian
PRETTY_NAME="Ubuntu 15.04"
VERSION_ID="15.04"
HOME_URL="http://www.ubuntu.com/"
SUPPORT_URL="http://help.ubuntu.com/"
BUG_REPORT_URL="http://bugs.launchpad.net/ubuntu/"
```

# REQUIREMENTS

* [Docker](https://www.docker.com/)

## Optional

* [make](http://www.gnu.org/software/make/)
* [Node.js](https://nodejs.org/en/) (for dockerlint)

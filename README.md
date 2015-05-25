# docker-ubuntu-32bit - Docker base images for 32bit Ubuntu

# ABOUT

docker-ubuntu-32bit is a collection of [debootstrap](https://wiki.debian.org/Debootstrap)-generated 32-bit Ubuntu base images.

# DOCKER HUB

https://registry.hub.docker.com/u/mcandre/docker-ubuntu-32bit/

# EXAMPLE

```
$ make
docker run --rm --privileged -v $(pwd):/mnt -t ubuntu:15.04 sh -c 'apt-get update && apt-get install -y debootstrap && mkdir /chroot && debootstrap --arch i386 karmic /chroot http://old-releases.ubuntu.com/ubuntu/ && cd /chroot && tar czvf /mnt/rootfs.tar.gz .'
...

docker build -t mcandre/docker-ubuntu-32bit:9.10 .
Step 0 : FROM scratch
Step 1 : MAINTAINER Andrew Pennebaker <andrew.pennebaker@gmail.com>
Step 2 : ADD rootfs.tar.gz /
Successfully built babc33fdd1bd

docker run --rm mcandre/docker-ubuntu-32bit:9.10 sh -c 'cat /etc/*release*'
DISTRIB_ID=Ubuntu
DISTRIB_RELEASE=9.10
DISTRIB_CODENAME=karmic
DISTRIB_DESCRIPTION="Ubuntu 9.10"
```

# REQUIREMENTS

* [Docker](https://www.docker.com/)

## Optional

* [make](http://www.gnu.org/software/make/)

## Debian/Ubuntu

```
$ sudo apt-get install docker.io build-essential
```

## RedHat/Fedora/CentOS

```
$ sudo yum install docker-io
```

## non-Linux

* [VirtualBox](https://www.virtualbox.org/)
* [Vagrant](https://www.vagrantup.com/)
* [boot2docker](http://boot2docker.io/)

### Mac OS X

* [Xcode](http://itunes.apple.com/us/app/xcode/id497799835?ls=1&mt=12)
* [Homebrew](http://brew.sh/)
* [brew-cask](http://caskroom.io/)

```
$ brew cask install virtualbox vagrant
$ brew install boot2docker
```

### Windows

* [Chocolatey](https://chocolatey.org/)

```
> chocolatey install docker make
```

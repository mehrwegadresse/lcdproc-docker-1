# LCDproc - Multi-platform LCD display driver

This is a docker image for [LCDproc](https://github.com/lcdproc/lcdproc) based
on the offical Debian packages.


## Tagged Docker Images

Images are tagged according to the installed LCDproc version. All images are build using Debain GNU/Linux.

* [`0.5.7`, `latest` Dockerfile](https://github.com/liske/lcdproc-docker/blob/master/lcdproc-0.5.7-debian/Dockerfile)

  [![Layers](https://images.microbadger.com/badges/image/liske/lcdproc:latest.svg)](https://images.microbadger.com/badges/image/liske/lcdproc:latest)
  This image is build using *Debian stretch* and should be considered **stable**.

* [`0.5.9` Dockerfile](https://github.com/liske/lcdproc-docker/blob/master/lcdproc-0.5.9-debian/Dockerfile)

  [![Layers](https://images.microbadger.com/badges/image/liske/lcdproc:0.5.9.svg)](https://images.microbadger.com/badges/image/liske/lcdproc:0.5.9)
  This image is build using *Debian buster* and should be considered **unstable**.


* [`0.5.5` Dockerfile](https://github.com/liske/lcdproc-docker/blob/master/lcdproc-0.5.5-debian/Dockerfile)

  [![Layers](https://images.microbadger.com/badges/image/liske/lcdproc:0.5.5.svg)](https://images.microbadger.com/badges/image/liske/lcdproc:0.5.5)
  This image is build using *Debian wheezy* and should be considered **obsolete**.


## Usage

The default command runs `LCDd` in foreground. You need to override the command to run `lcdproc` (see also *docker-compose.yml example*).

### docker run

```
$ docker run --rm -v /path/to/conf/LCDd.conf:/etc/LCDd.conf:ro -p 13666 --privileged liske/lcdproc
```

### docker-compose

```
# docker-compose.yml example
version: '3'
services:
  lcdd:
    image: liske/lcdproc
    volumes:
      - /path/to/conf/LCDd.conf:/etc/LCDd.conf:ro
    ports:
      - 13666:13666
    privileged: true
    restart: always

  lcdproc:
    image: liske/lcdproc
    command: [ "lcdproc", "-s", "lcdd", "-f", "-c", "/etc/lcdproc.conf", "L" ]
    hostname: myhostname
    volumes:
      - /path/to/conf/lcdproc.conf:/etc/lcdproc.conf:ro
    restart: always
    depends_on:
      - lcdd
```

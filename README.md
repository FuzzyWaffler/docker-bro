![bro-logo](https://github.com/blacktop/docker-bro/raw/master/docs/imgs/logo.png)

Bro IDS Dockerfile
==================

[![CircleCI](https://circleci.com/gh/blacktop/docker-bro.png?style=shield)](https://circleci.com/gh/blacktop/docker-bro) [![License](http://img.shields.io/:license-mit-blue.svg)](http://doge.mit-license.org) [![Docker Stars](https://img.shields.io/docker/stars/blacktop/bro.svg)](https://hub.docker.com/r/blacktop/bro/) [![Docker Pulls](https://img.shields.io/docker/pulls/blacktop/bro.svg)](https://hub.docker.com/r/blacktop/bro/) [![Docker Image](https://img.shields.io/badge/docker image-21.9 MB-blue.svg)](https://hub.docker.com/r/blacktop/bro/)

This repository contains a **Dockerfile** of [Bro-IDS](http://www.bro.org/index.html) **blacktop/bro**.

**Table of Contents**

-	[Dependencies](#dependencies)
-	[Image Tags](#image-tags)
-	[Installation](#installation)
-	[Getting Started](#getting-started)
-	[Documentation](#documentation)
-	[Issues](#issues)
-	[Todo](#todo)
-	[CHANGELOG](#changelog)
-	[Contributing](#contributing)
-	[License](#license)

### Dependencies

-	[gliderlabs/alpine:3.4](https://index.docker.io/_/gliderlabs/alpine/)

### Image Tags

```bash
$ docker images

REPOSITORY          TAG                 SIZE
blacktop/bro        latest              21.9 MB
blacktop/bro        2.5                 21.9 MB
blacktop/bro        elastic             59.45 MB
blacktop/bro        geoip               55.97 MB
blacktop/bro        kafka               28.91 MB
blacktop/bro        2.4.1               16.68 MB
blacktop/bro        2.4                 16.68 MB
```

> **NOTE:**
 * tag **elastic** is the same as tag **2.5**, but includes the **elasticsearch plugin** and the **GeoIP** database  
 * tag **kafka** is the same as tag **2.5**, but includes the **kafka plugin**  
 * tag **geoip** is the same as tag **2.5**, but includes the **GeoIP** database  
 * **all** tags include the **af_packet plugin**

### Installation

1.	Install [Docker](https://docs.docker.com).
2.	Download [trusted build](https://hub.docker.com/r/blacktop/bro/) from public [Docker Registry](https://hub.docker.com): `docker pull blacktop/bro`

### Getting Started

```bash
$ wget https://github.com/blacktop/docker-bro/raw/master/pcap/heartbleed.pcap
$ docker run --rm -v `pwd`:/pcap \
         blacktop/bro -r heartbleed.pcap local "Site::local_nets += { 192.168.11.0/24 }"
```

```bash
$ ls -l

-rw-r--r--  1 blacktop  staff   635B Jul 30 12:11 conn.log
-rw-r--r--  1 blacktop  staff   754B Jul 30 12:11 files.log
-rw-r--r--  1 blacktop  staff   384B Jul 30 12:11 known_certs.log
-rw-r--r--  1 blacktop  staff   239B Jul 30 12:11 known_hosts.log
-rw-r--r--  1 blacktop  staff   271B Jul 30 12:11 known_services.log
-rw-r--r--  1 blacktop  staff    17K Jul 30 12:11 loaded_scripts.log
-rw-r--r--  1 blacktop  staff   1.9K Jul 30 12:11 notice.log <====== NOTICE
-rw-r--r--  1 blacktop  staff   253B Jul 30 12:11 packet_filter.log
-rw-r--r--  1 blacktop  staff   1.2K Jul 30 12:11 ssl.log
-rw-r--r--  1 blacktop  staff   901B Jul 30 12:11 x509.log
```

```bash
$ cat notice.log | awk '{ print $11 }' | tail -n4

Heartbleed::SSL_Heartbeat_Attack
Heartbleed::SSL_Heartbeat_Odd_Length
Heartbleed::SSL_Heartbeat_Attack_Success
```

### Documentation

-	[Usage](https://github.com/blacktop/docker-bro/blob/master/docs/usage.md)
-	[Integrate with the Elastic Stack](https://github.com/blacktop/docker-bro/blob/master/docs/elastic.md)
-	[Integrate with Kafka](https://github.com/blacktop/docker-bro/blob/master/docs/kafka.md)
-	[Tips and Tricks](https://github.com/blacktop/docker-bro/blob/master/docs/tips-and-tricks.md)

### Issues

Find a bug? Want more features? Find something missing in the documentation? Let me know! Please don't hesitate to [file an issue](https://github.com/blacktop/docker-bro/issues/new) and I'll get right on it.

### Todo

-	[x] Install/Run Bro-IDS
-	[x] Fix Geolocation feature
-	[x] Refine my extract-all.bro script
-	[x] Start Daemon and watch folder with `inotify`
-	[x] Add ELK Stack

### Credits

Alpine conversion heavily (if not entirely) influenced by https://github.com/nizq/docker-bro

### CHANGELOG

See [`CHANGELOG.md`](https://github.com/blacktop/docker-bro/blob/master/CHANGELOG.md)

### Contributing

[See all contributors on GitHub](https://github.com/blacktop/docker-bro/graphs/contributors).

Please update the [CHANGELOG.md](https://github.com/blacktop/docker-bro/blob/master/CHANGELOG.md) and submit a [Pull Request on GitHub](https://help.github.com/articles/using-pull-requests/).

### License

MIT Copyright (c) 2015-2017 **blacktop**

# Munin Server

<!--
[![Docker Stars](https://img.shields.io/docker/stars/jekil/docker-munin-server.svg)](https://hub.docker.com/r/jekil/docker-munin-server/)
[![Docker Pulls](https://img.shields.io/docker/pulls/jekil/docker-munin-server.svg)](https://hub.docker.com/r/jekil/docker-munin-server/)
[![Image Size](https://img.shields.io/imagelayers/image-size/jekil/docker-munin-server/latest.svg)](https://imagelayers.io/?images=jekil/docker-munin-server:latest)
[![Image Layers](https://img.shields.io/imagelayers/layers/jekil/docker-munin-server/latest.svg)](https://imagelayers.io/?images=jekil/docker-munin-server:latest)
[![Twitter Follow](https://img.shields.io/twitter/follow/jekil.svg?style=social)](https://twitter.com/jekil)
-->

This image provides a munin server, configured as CGI, using nginx.
It can be totally configured by command line, passing the hosts you want to monitor as argument.

---

**This image forked from `jekil/docker-munin-server`. There are two overwrote points.**

1. **Supported `notify_slack_munin` command**  => Enable to nitify slack
2. **Added `munin-ctrl` command**  => Easy to manage munin-server
3. **Changed default theme**  => Twitter Bootstrap based theme

<!--

## Quick Start

Use the following command to start the munin server, in the NODES argument you should supply a space separated list of `<name>:<host>` munin node pairs. (i.e. `foo.local:127.0.0.1 bar.remote:1.2.3.4`)

`docker run -p 80 -e NODES="foo.local:127.0.0.1 bar.remote:1.2.3.4" munin`

-->

## Usage

[1] Configure munin settings on `munin.conf`

```shell
vi data/conf/munin.conf
```

[2] Configure slack settings on `notify_slack_munin`

```shell
vi notify_slack_munin
```

[3] Execute following commands

```shell
# build
sudo docker build -t munin-server .
# start
sudo ./munin-ctrl start
# stop
sudo ./munin-ctrl stop
```

## Technical details

Ports exposed:

* 80

Environment Variables :

* `NODES`: Space separated list of `<name>:<host>` munin node pairs. (i.e. `foo.local:127.0.0.1 bar.remote:1.2.3.4`)

Volumes:

* /var/lib/munin
* /var/log/munin
* /etc/munin

---
title: use docker build a VPN server for mac
date: 2019-02-12 22:31:07
updated: 2019-02-12 22:31:07
tags: [docker,centos]
---

#### 1. create vpn setting
$ vim ~/workspace/docker/vpn/env

```
VPN_IPSEC_PSK=someword_pre_shared_key
VPN_USER=username
VPN_PASSWORD=userpwd
```
<!--more-->

---

#### 2. load the IPsec `af_key` kernel module on the Docker host.

```
sudo modprobe af_key
```

#### 2.1 load it on startup (centos)
$ vim /etc/modules-load.d/af_key.conf
```
# Load af_key at boot
af_key
```

##### * To ensure that this kernel module is loaded on boot, please refer to: [Ubuntu/Debian](https://help.ubuntu.com/community/Loadable_Modules), [CentOS 6](https://access.redhat.com/documentation/en-us/red_hat_enterprise_linux/6/html/deployment_guide/sec-persistent_module_loading), [CentOS 7](https://access.redhat.com/documentation/en-US/Red_Hat_Enterprise_Linux/7/html/Kernel_Administration_Guide/sec-Persistent_Module_Loading.html), [Fedora](https://docs.fedoraproject.org/en-US/fedora/f28/system-administrators-guide/kernel-module-driver-configuration/Working_with_Kernel_Modules/index.html#sec-Persistent_Module_Loading) and [CoreOS](https://coreos.com/os/docs/latest/other-settings.html).

---

#### 3. Create a new Docker container from this image (replace `~/.../vpn/env` with your own `env` file):

```
$ docker run \
    --name ipsec-vpn-server \
    --env-file ~/workspace/docker/vpn/env \
    --restart=always \
    -p 500:500/udp \
    -p 4500:4500/udp \
    -v /lib/modules:/lib/modules:ro \
    -d --privileged \
    hwdsl2/ipsec-vpn-server
```
---

#### View log
```
$ docker logs ipsec-vpn-server
```

#### Check server status
```
  $ docker exec -it ipsec-vpn-server ipsec status
```

#### display current established VPN connections:
```
  $ docker exec -it ipsec-vpn-server ipsec whack --trafficstatus
```

---

#### How to setting on mac ?
```
VPN_USER=username
```
{% asset_img 1.png "username" %}

```
VPN_PASSWORD=userpwd
VPN_IPSEC_PSK=someword_pre_shared_key
```
{% asset_img 2.png "VPN_IPSEC_PSK and VPN_PASSWORD" %}

---

reference :
[docker-ipsec-vpn-server](https://github.com/hwdsl2/docker-ipsec-vpn-server/blob/master/README.md)

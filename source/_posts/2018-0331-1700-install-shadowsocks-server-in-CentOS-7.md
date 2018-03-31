---
title: install shadowsocks server in CentOS 7
date: 2018-03-31 17:00:00
tags: [linux,centos]
---

shadowsocks is an open-source encrypted proxy project,
usually use to pass GFA (Great Firewall of China)

<!--more-->

1. add repo to yum
```
cd /etc/yum.repos.d/
curl -O https://copr.fedorainfracloud.org/coprs/librehat/shadowsocks/repo/epel-7/librehat-shadowsocks-epel-7.repo
yum install -y shadowsocks-libev
```

2. edit config
```
$vim /etc/shadowsocks-libev/config.json

{
    "server": "0.0.0.0",
    "server_port": 3389,
    "password": "login_password",
    "method":"aes-256-cfb",
    "mode": "tcp_and_udp",
    "timeout":3600
}
```

3. check config workfine
```
ss-server -c /etc/shadowsocks-libev/config.json
```
4. start service
systemctl restart shadowsocks-libev
systemctl enable shadowsocks-libev

5. check log
```
journalctl -u shadowsocks-libev
tail -f /var/log/messages
tail -f /var/log/secure
```

* if get this message :
```
ss-local: error while loading shared libraries: libmbedcrypto.so.0: cannot open shared object file: No such file or directory
```

install "mbedtls-devel"
```
$ yum install mbedtls-devel
$ cd /usr/lib64
$ ls |grep mbed
$ ln -sf libmbedcrypto.so.1 libmbedcrypto.so.0
```

reference:
https://zzz.buzz/zh/gfw/2017/08/14/install-shadowsocks-server-on-centos-7/
https://github.com/shadowsocks/shadowsocks-libev/issues/1966


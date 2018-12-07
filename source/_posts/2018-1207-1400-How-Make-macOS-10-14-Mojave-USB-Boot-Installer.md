---
title: How Make macOS 10.14 Mojave USB Boot Installer
date: 2018-12-07 14:00:00
updated: 2018-12-07 14:00:00
tags: [osx]
---

Finally i update my mac to 10.14
and i use that image make a USB bootable install loader.

Here is the step
-----

0. [ download / update ] Mojave from Mac app stroe
{% asset_img 1.png "download it" %}

<!--more-->

1. when downloa was ready and show this window, `DO NOT` Click `continue`.
{% asset_img 2.png "Mojave install screen" %}

2. open finder, and find out your "applications" directory,
   now you can see the file "Install macOS Mojave.app".
{% asset_img 3.png "copy to your directory" %}

3. backup to your other directory

4. Plug USB driver, and format it

5. Open terminal and paste the commend on below
   and replace {xxxx} to your path.

```
sudo /{File Path}/Install\ macOS\ Mojave.app/ \
Contents/Resources/createinstallmedia \
--volume /Volumes/{USB Name}/ \
--applicationpath /{File Path}/Install\ macOS\ Mojave.app/ \
--nointeraction
```

6. then system will start make usb bootable install leader




How to use it?
-----

0. when mac is power off

1. plug usb driver

2. hold `option` key

3. power on

4. select the USB install leader to boot up

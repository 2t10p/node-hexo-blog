---
title: How Make macOS 10.15 Catalina USB Boot Installer
date: 2019-10-10 15:11:03
updated: 2019-10-10 15:11:03
tags: [osx]
---

Apple release macOS 10.15 Catalina
and i'm trying use that image make a USB bootable install loader.

Here is the step
-----

0. [ download / update ] macOS 10.15 Catalina from Mac app stroe or systen update
{% asset_img 1.png "download it" %}

<!--more-->

1. when downloa was ready and show this window, `DO NOT` Click `continue`.
{% asset_img 2.png "install screen" %}

2. open finder, and go "applications" directory on your `finder`,
   now you can see the file "Install macOS Catalina.app".
{% asset_img 3.png "copy to your directory" %}

3. backup to your other directory

4. Plug USB driver, and format it

5. Open terminal and paste the commend on below
   and replace {xxxx} to your path.

```
sudo /{File_Path}/Install\ macOS\ Catalina.app/Contents/Resources/createinstallmedia \
--volume /Volumes/{USB_Name}/ \
--nointeraction \
--downloadassets
```

6. then system will start make usb bootable install leader
{% asset_img 4.png "process screen" %}

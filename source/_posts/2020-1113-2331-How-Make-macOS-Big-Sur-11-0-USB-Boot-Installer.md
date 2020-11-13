---
title: How Make macOS Big Sur 11.0 USB Boot Installer
date: 2020-11-13 23:31:12
updated: 2020-11-13 23:31:12
tags: [osx]
---

Apple release Big update macOS Big Sur 11.0 today !

let's make a make a USB bootable install loader for backup.


Here is the step
-----

0. [ download / update ] macOS Big Sur 11.0 from `App Stroe` or `Systen Update`
{% asset_img 1.png "download it" %}
{% asset_img 2.png "download it" %}

<!--more-->

1. when download was done and show this window, `DO NOT` click `continue`.
{% asset_img 3.png "install window" %}

2. open finder, and go "applications" directory on your `finder`,
   now you can see the file "Install macOS Catalina.app".
{% asset_img 4.png "find OS insatll app from applications" %}

3. copy it to other directory
{% asset_img 5.png "copy OS insatll app to your directory" %}

4. Plug USB driver, and format it

5. Open terminal and paste the commend on below
   and replace `{xxxx}` to your path. (please sure the `path` is correct)

```
sudo /{File_Path}/Install\ macOS\ Big\ Sur.app/Contents/Resources/createinstallmedia \
--volume /Volumes/{USB_Name}/ \
--nointeraction \
--downloadassets
```

6. then system will start make usb bootable install leader
{% asset_img 5.png "process screen" %}

7. now you can use this usb to boot
   and hold `Cmd(⌘) + R`
   to get into `install OS mode` or `recover mode`.

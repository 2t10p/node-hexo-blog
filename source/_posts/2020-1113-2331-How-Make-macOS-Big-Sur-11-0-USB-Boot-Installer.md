---
title: How Make macOS Big Sur 11.0 USB Boot Installer
date: 2020-11-13 23:31:12
updated: 2020-11-13 23:31:12
tags: [osx]
---

Apple release Big update `macOS Big Sur (11.0)` today.
Let's make a make a USB bootable install loader for backup.

---

### Step :

#### 1. Download macOS Big Sur 11.0 from `App Stroe` or `Systen Update`

{% asset_img 1.png "download it" %}

<!--more-->
{% asset_img 2.png "download it" %}

#### 2. When download was done and show this window, `DO NOT` click `continue`.
{% asset_img 3.png "install window" %}

#### 3. Open finder, and go "applications" directory on your `finder`,now you can see the file "Install macOS Catalina.app".
{% asset_img 4.png "find OS insatll app from applications" %}

#### 4. Copy it to other directory

#### 5. Plug USB driver, and format it

#### 6. change this command, replace `{xxxx}` to your system path.
```
sudo /{File_Path}/Install\ macOS\ Big\ Sur.app/Contents/Resources/createinstallmedia \
--volume /Volumes/{USB_Name}/ \
--nointeraction \
--downloadassets
```

####7. Open terminal and run that command (Be sure the `path` is correct)


####8. then system will start make usb bootable install leader
{% asset_img 5.png "process screen" %}

####9. now you can boot with this usb and hold `Cmd(⌘) + R` to get into `install OS mode` or `recover mode`.

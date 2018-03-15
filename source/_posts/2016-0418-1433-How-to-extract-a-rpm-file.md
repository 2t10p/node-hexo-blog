---
title: How to extract a rpm file
date: 2016-04-18 14:27:20
tags: [linux]
---

someting you need check a rpm file, but do not wanna install rpm,

can use this command extract to a directory.
<!--more-->

    rpm2cpio {whatYouWantExtract}.rpm | cpio -idmv


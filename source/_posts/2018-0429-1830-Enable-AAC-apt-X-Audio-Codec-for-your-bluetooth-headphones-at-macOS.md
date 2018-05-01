---
title: Enable AAC/apt-X Audio Codec for your bluetooth headphones at macOS
date: 2018-04-29 18:30:00
updated: 2018-04-29 18:30:00
tags: [osx]
---

at macOS usually your headphone bluetooth codec is not active,
(only enable when you are use apple's product)

how to check it ?

1. start a player
   (because codec only active when headphone playing sound)

2. hold the "option" key and click bluetooth icon on system bar

3. check what the active codec status now

{% asset_img 1.png "codec not active" %}

<!--more-->

if it is disable

you can use this command to enable it

```
sudo defaults write bluetoothaudiod "Enable AptX codec" -bool true 
sudo defaults write bluetoothaudiod "Enable AAC codec" -bool true 
```

and restart your bluetooth, now it should work
{% asset_img 2.png "codec not active" %}



if you wanna set back to default just set true to false

```
sudo defaults write bluetoothaudiod "Enable AptX codec" -bool false 
sudo defaults write bluetoothaudiod "Enable AAC codec" -bool false
```

reference : 
[macrumors](https://www.macrumors.com/how-to/enable-aptx-aac-bluetooth-audio-codecs-macos/)

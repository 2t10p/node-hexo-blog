---
title: How to capture youtube livestream to mp4 (or mp3) on mac
date: 2019-04-13 23:11:03
updated: 2019-04-13 23:11:03
tags: [osx]
---

* install [homebrew](https://docs.brew.sh/Installation)
&nbsp;

* use brew install streamlink
```
$ brew install streamlink
```
&nbsp;

* download youtube livestream
```
$ streamlink --hls-live-restart -o 'out.m3u8' 'https://www.youtube.com/watch?v=xxxxxxxxxxx' best
```
&nbsp;

* use brew install ffmpeg
```
$ brew install ffmpeg
```
&nbsp;

* convert hls(m3u8) to mp4
```
$ ffmpeg -i in.m3u8 -acodec copy -bsf:a aac_adtstoasc -vcodec copy out.mp4
```
&nbsp;

* convert mp4 to mp3
```
$ ffmpeg -i out.mp4 -q:a 0 -map a out.mp3
```
&nbsp;

* crop mp3 from 60s to 60+120s
```
$ ffmpeg -ss 60 -t 120 -i in.mp3 -acodec copy out.mp3
```
&nbsp;

ref:
https://streamlink.github.io/cli.html
https://github.com/ytdl-org/youtube-dl/issues/11618
https://stackoverflow.com/questions/33108105/converting-an-hls-m3u8-to-mp4
https://superuser.com/questions/332347/how-can-i-convert-mp4-video-to-mp3-audio-with-ffmpeg
https://stackoverflow.com/questions/1390731/how-to-crop-a-mp3-from-x-to-xn-using-ffmpeg

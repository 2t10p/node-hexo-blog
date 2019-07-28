# node-hexo-blog
Github page backup

# new a post
npm run hexo new "YYYY-MMDD-HHMM-Post title"

# publish to github page
npm run publish

# publish and update github
npm run publish && git add . && git commit -m 'add post' && gitpushom

# create new post
npm run hexo new "YYYY-MMDD-HHMM-Post title"

# template
---
title: Post title
date: YYYY-MM-DD HH:MM:SS
updated: YYYY-MM-DD HH:MM:SS
tags: [tag1, tag2]
---

newline
&nbsp;

show a link
[github](https://github.com)

show a image [that image in some name folder]
{% asset_img 1.png "image description" %}

show "read more"
<!--more-->

fancybox
![img caption](img url)

{% fancybox img_url [img_thumbnail] [img_caption] %}

# publish to github page
npm run publish


reference :
[github](https://github.com)

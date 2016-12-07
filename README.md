# node-hexo-blog
Github page backup

# new a post
npm run hexo new "YYYY-MMDD-HHMM-Post title"

# publish to github page
npm run publish

# template

    ---
    title: Post title
    date: YYYY-MM-DD HH:MM:SS
    tags: [tag]
    ---

    show a link
    [github](https://github.com)

    show a image [that image in some name folder]
    {% asset_img 1.png "image description" %}

    show "read more"
    <!--more-->


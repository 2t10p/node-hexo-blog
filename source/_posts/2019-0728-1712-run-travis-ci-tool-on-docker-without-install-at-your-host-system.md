---
title: run travis-ci tool on docker without install at your host system
date: 2019-07-28 17:12:03
updated: 2019-07-28 17:12:03
tags: [continuous-integration, docker]
---

when use travis-ci to do auto deploy,
some time you want `crypto some string` like s3 bucket key ... etc
&nbsp;
travis ci provide a tools [Travis Client](https://github.com/travis-ci/travis.rb#readme) that can let you encrypt data
but need install ruby & gem to your global system, really dont like this way.
&nbsp;
so i use docker to do it.
&nbsp;
<!--more-->
1. start a ruby contener & install travis tools
```
$ docker pull ruby
$ docker run -ti --rm ruby bash
```
&nbsp;
2. install travis tools & login
```
$ gem install travis
$ travis login --pro
```
&nbsp;
3. encrypt data what you want, only can use on specific github repo
```
$ travis encrypt "some_string_you_want_encrypt" -r wicowen/demo-repo
```
&nbsp;
4. paste result to `travis.yml`
```
notifications:
  slack:
    rooms:
      secure: "JRPbbsQ...............="
    on_success: always
    on_failure: always

```

&nbsp;
&nbsp;
ref:
https://github.com/travis-ci/travis.rb#readme
https://docs.travis-ci.com/user/encryption-keys/

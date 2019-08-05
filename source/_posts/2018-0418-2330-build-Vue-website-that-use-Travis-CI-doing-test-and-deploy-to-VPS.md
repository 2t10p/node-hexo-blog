---
title: Build Vue website that use Travis CI doing test and deploy to VPS
date: 2018-04-18 23:30:00
updated: 2018-04-20 11:16:00
tags: [vue,nginx,centos,continuous-integration,continuous-delivery]
---

i build a side project use vue cli

that can easily create a basic frontend web site
with alot morden tools (js lint, unit test, e2e test ... etc)

here is some note for trying integration whole project

the workflow is

1. send a commit to github repo

2. travis-ci get the repo update then start build task

3. after task done without error

4. run deploy shell,

5. login to vps server use encrypted ssh key

6. push local tested repo to vps

<!--more-->

reference :
Deploy static sites to Digital Ocean with Travis CI
https://monicalent.com/blog/2017/12/21/deploy-static-sites-digital-ocean-travis/
https://medium.com/@tibotiber/deployment-of-static-websites-to-digital-ocean-using-travisci-957e6e0f1f9d
https://kjaer.io/travis/

Auto Authorize SSH Auth Requests on Travis CI
https://stackoverflow.com/questions/16638573/auto-authorize-ssh-auth-requests-on-travis-ci

Travis CI skip_cleanup
https://docs.travis-ci.com/user/deployment#Uploading-Files-and-skip_cleanup

Karma - change to chrome headless
https://developers.google.com/web/updates/2017/06/headless-karma-mocha-chai
http://karma-runner.github.io/0.13/config/browsers.html

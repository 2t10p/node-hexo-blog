---
title: start/stop all docker container at once
date: 2016-04-10 01:06:56
tags: [docker]
---

sometime you wanna start/stop all docker,
you can try this command.
<!--more-->

    docker start $(docker ps -aq)
    docker stop $(docker ps -aq)


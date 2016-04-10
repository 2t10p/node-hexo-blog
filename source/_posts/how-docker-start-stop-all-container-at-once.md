---
title: how docker start/stop all container at once
date: 2016-04-10 01:06:56
tags: [docker]
---

sometime you wanna stop all docker,
you can try this command.

    docker start $(docker ps -aq)
    docker stop $(docker ps -aq)


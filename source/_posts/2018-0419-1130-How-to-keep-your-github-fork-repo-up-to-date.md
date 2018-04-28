---
title: How to keep your github fork repo up to date
date: 2018-04-19 11:30:00
updated: 2018-04-19 11:30:00
tags: [git]
---


### 1. Clone your fork:

    git clone git@github.com:YOUR-USERNAME/YOUR-FORKED-REPO.git

### 2. Add remote from original repository in your forked repository: 

    cd into/cloned/fork-repo
    git remote add upstream git://github.com/ORIGINAL-DEV-USERNAME/REPO-YOU-FORKED-FROM.git
    git fetch upstream

### 3. Updating your fork from original repo to keep up with their changes:

    git pull upstream master

reference :
https://gist.github.com/CristinaSolana/1885435

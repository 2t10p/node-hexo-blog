---
title: tmux scroll up at mac terminal
date: 2016-04-23 15:50:47
tags:
---

at mac terminal,
when you at tmux,
cant use scroll up and down to watch scrollback buffer

How to fix ?
add this line to ~/.tmux.conf

    set -g terminal-overrides 'xterm*:smcup@:rmcup@'


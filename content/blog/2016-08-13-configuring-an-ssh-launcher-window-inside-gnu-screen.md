---
title: "Binding an SSH Launcher to a GNU Screen Hotkey"
date: 2016-08-13
author: "Aleksey Tsalolikhin"
---

Two lines added to .screenrc:

1. A launcher window: `screen -t launcher /bin/sh -c 'while true; do echo -n "Hostname: "; read host; screen -t $host ssh $host; clear; done'`

2. A keybinding: `bindkey "13" select 0` — maps Ctrl-K to switch to the launcher window.

Pressing Ctrl-K and entering a hostname automatically creates a new GNU Screen window titled with that hostname and initiates SSH.

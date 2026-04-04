---
title: "Using Ansible to Change sshd Configuration"
date: 2016-07-28
author: "Aleksey Tsalolikhin"
---

A developer asked to activate two SSH config options on multiple servers:

- ClientAliveInterval 15
- ClientAliveCountMax 3

These help maintain active SSH connections during debugging sessions.

Solution: Ansible's raw mode (no Python required on target hosts — executes shell commands directly).

## Steps

1. Verify current commented-out settings via grep across all target servers
2. Use sed to uncomment the configuration lines
3. Validate changes were applied
4. Reload sshd: /etc/init.d/sshd reload

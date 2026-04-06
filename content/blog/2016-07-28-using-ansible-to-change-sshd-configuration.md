---
title: "Using Ansible to change sshd configuration"
date: 2016-07-28
---

One of my clients is at the ssh "for" loop stage of automation maturity, so I installed Ansible. Because of selinux and Python version issues, I'm using the "raw" mode (which doesn't require Python on the hosts, it just runs raw shell commands).

What follows is an example of using Ansible raw mode to make changes at scale.

## Problem

A developer requested:

> Please, activate these option on XYZ servers in the /etc/ssh/sshd\_config so I can stay connected while debugging:
> 
> ClientAliveInterval 15 ClientAliveCountMax 3

## Solution

First, check current setting, so that I know what we have in place now (starting point):

```
$ ansible all -i /tmp/hosts  -m raw -a "grep ClientAliveCountMax /etc/ssh/sshd_config"  --ask-pass --one-line --user=root
SSH password:
X | success | rc=0 | (stdout) #ClientAliveCountMax 3

Y | success | rc=0 | (stdout) #ClientAliveCountMax 3

Z | success | rc=0 | (stdout) #ClientAliveCountMax 3

$
```

Uncomment the line, enabling the setting:

```
$ ansible all -i /tmp/hosts -m raw -a "sed -i /etc/ssh/sshd_config -e 's:.ClientAliveCountMax 3:ClientAliveCountMax 3:'; grep ClientAliveInterval /etc/ssh/sshd_config"  --ask-pass --one-line --user=root

$ ansible all -i /tmp/hosts -m raw -a "grep ClientAliveCountMax /etc/ssh/sshd_config" --ask-pass --one-line --user=root
SSH password:
X | success | rc=0 | (stdout) ClientAliveCountMax 3

Y | success | rc=0 | (stdout) ClientAliveCountMax 3

Z | success | rc=0 | (stdout) ClientAliveCountMax 3

$
```

Summary of changes: - **Before:** #ClientAliveCountMax 3 - **After:** ClientAliveCountMax 3

Rince and repeat for ClientAliveInterval.

Now reload SSHd config:

```
$ ansible all -i /tmp/hosts -m raw -a "/etc/init.d/sshd reload"  --ask-pass --one-line --user=root
SSH password:
X | success | rc=0 | (stdout) Reloading sshd: [  OK  ]

Y | success | rc=0 | (stdout) Reloading sshd: [  OK  ]

Z | success | rc=0 | (stdout) Reloading sshd: [  OK  ]

$
```

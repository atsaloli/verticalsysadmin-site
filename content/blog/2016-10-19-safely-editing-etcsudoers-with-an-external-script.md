---
title: "Safely updating /etc/sudoers non-interactively"
date: 2016-10-19
---

I recently added my account to /etc/sudoers on N servers using Ansible in raw mode (running a shell oneliner). We use visudo to edit /etc/sudoers when we are logged into a server, but since I was doing this in "batch" mode I wanted to do it non-interactively but still have the benefit of the file-locking and syntax checking and rollback that visudo provides. So I set visudo's VISUAL environment variable to my external command:

`[root@myhost ansible]# more sudoers.sh grep -q ^tsalolia /etc/sudoers || VISUAL="(echo /^root; echo a; echo 'tsalolia ALL=(ALL) ALL'; echo .; echo 'g/^#tsalolia/d'; echo 'x!') | ex - /etc/sudoers" visudo visudo -c [root@myhost ansible]#`

I edited /etc/sudoers directly with ex to append my entry below root's because every host had a different /etc/sudoers file (this is what happens when you don't have configuration management).

Long-term, I'm planning to templatize /etc/sudoers at this client.

I should be able to run

`VISUAL="cp /etc/sudoers.new /etc/sudoers" visudo`

to safely install the new sudoers file.

P.S. I developed the above on CentOS 5 and 6, but when I tried it on Ubuntu 16, I got the error: `visudo: specified editor ((echo /^root; echo a; echo 'tsalolia ALL=(ALL) ALL'; echo .; echo 'g/^#tsalolia/d'; echo 'x!') | ex - /etc/sudoers) doesn't exist`

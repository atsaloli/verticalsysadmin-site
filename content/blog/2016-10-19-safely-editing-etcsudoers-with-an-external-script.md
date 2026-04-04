---
title: "Safely Updating /etc/sudoers Non-Interactively"
date: 2016-10-19
author: "Aleksey Tsalolikhin"
---

Describes updating /etc/sudoers in batch mode while retaining visudo's safety features (file-locking, syntax checking, automatic rollback). Needed to add an account across multiple servers using Ansible.

Solution: set the VISUAL environment variable to a custom ex-based command:

```bash
grep -q ^tsalolia /etc/sudoers || VISUAL="(echo /^root; echo a; echo 'tsalolia ALL=(ALL) ALL'; echo .; echo 'g/^#tsalolia/d'; echo 'x!') | ex - /etc/sudoers" visudo
```

Long-term plan: templatize /etc/sudoers across the org, then simply use `VISUAL="cp /etc/sudoers.new /etc/sudoers" visudo`.

Caveat: worked on CentOS 5 and 6 but failed on Ubuntu 16.

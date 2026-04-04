---
title: "CFEngine and Ansible are complementary"
date: 2016-02-18
author: "Aleksey Tsalolikhin"
---

CFEngine and Ansible serve different purposes and work well together.

**CFEngine strength:** Ongoing maintenance and verification of desired state. Example: CFEngine Enterprise report revealed [CliQr](http://www.cliqr.com) version distribution across all systems almost instantly.

**Ansible strength:** Ad-hoc, one-time checks. Example: quickly verify whether a specific symlink existed across all hosts in preparation for a CliQr upgrade.

**Complementary use:** CFEngine keeps servers patched continuously; Ansible handles targeted actions like rebooting specific server groups during scheduled maintenance windows.

**Key insight:** CFEngine requires upfront investment to develop promises but provides ongoing automation. Ansible offers speed for immediate tasks but doesn't guarantee future compliance on systems that go offline.

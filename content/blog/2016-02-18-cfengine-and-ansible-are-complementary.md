---
title: "CFEngine and Ansible are complementary"
date: 2016-02-18
---

CFEngine is designed for ongoing maintenance and verification of desired state; whereas Ansible is designed as a simple tool for making changes quickly.

CFEngine and Ansible complement each other. For example, I have a CFEngine promise to inventory [CliQr](http://www.cliqr.com) version by reading in /usr/local/osmosix/MANIFEST.MF. By pulling up a CFEngine Enterprise report, I can tell in 3 seconds how many of my thousands of hosts are on which version of CliQr. To run this report with Ansible would take minutes (the more hosts, the longer it would take).

However to develop, test and deploy this CFEngine promise took its own time (an initial up-front investment).

Another example: I wanted to quickly check, just one time, in preparation for a CliQr upgrade (actual example) if /usr/local/osmosix/MANIFEST.MF is a symlink to /usr/local/osmosix/agent/MANIFEST.MF on ALL hosts, I used Ansible, as that was quicker than (a) writing a CFEngine promise and (b) scheduling a window to deploy it. Ansible is faster for an ad-hoc report like this.

However if I then wanted to ensure that symlink is present on all hosts (current and future), I’d use CFEngine, as doing it with Ansible would only reach the hosts up at that instant.

So these tools are complementary, and I intend to use them together. For example, CFEngine could keep servers up to date on patches but I’d use Ansible to reboot specific groups of servers during scheduled maintenance windows (to load the new patchset).

---
title: "Getting started with Infrastructure As Code"
date: 2010-09-15
author: "Aleksey Tsalolikhin"
---

Following a conversation with John Willis of Chef/OpsCode at Ohio Linux Fest (where the author had taught an introductory Cfengine 3 class), the author became enthusiastic about Infrastructure as Code.

Initial project: "I will roll out a new VM, completely configured by Cfengine, and the new application, also installed by Cfengine." Test in staging (ephemeral infrastructure), verify no additional manual steps needed, then discard the VM and replicate in production.

Represents a philosophical shift from traditional persistent infrastructure to dynamically provisioned, temporary systems managed entirely through code.

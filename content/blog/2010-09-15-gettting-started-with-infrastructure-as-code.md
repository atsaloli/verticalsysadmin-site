---
title: "Getting started with Infrastructure As Code"
date: 2010-09-15
---

After talking with John Willis of [Chef/OpsCode](http://www.opscode.com) at Ohio Linux Fest (I taught an intro class on Cfengine 3), I finally started to get Infrastructure As code.

Am immensely excited to try it out. My first project is to ephemerize the Web/App server tier in a staging environment - instead of rolling out a new version of the application, I will roll out a new VM, completely configured by Cfengine, and the new application, also installed by Cfengine.

The idea is, I will throw away the VM after the testing is complete. I will be sure that my Cfengine config is complete with no additional manual steps required to deploy a working version of the app.

The next step will be doing the same in production.

Bye bye being tied to a physical server. Hello virtualization and poof! pop! short-lived VM's.

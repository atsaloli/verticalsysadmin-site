---
title: "CFEngine Inventory of Windows Server 2012"
date: 2016-10-03
author: "Aleksey Tsalolikhin"
---

Building a centralized reporting portal for CFEngine Enterprise. CFEngine inventory on Windows collects: hostname, OS version, system manufacturer, disk utilization, hardware/IPv4 addresses, BIOS and architecture info, CFEngine version, unique ID, system uptime, serial number.

Technical note: after deploying a Windows Server 2012 VM in Joyent public cloud and bootstrapping it to the CFEngine hub, the hub couldn't collect reports until port 5308 was opened in Windows Firewall with Advanced Security.

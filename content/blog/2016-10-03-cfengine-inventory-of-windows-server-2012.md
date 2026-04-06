---
title: "CFEngine Inventory of Windows Server 2012"
date: 2016-10-03
---

I am working on setting up a "reporting portal" CFEngine Enterprise hub to aggregate inventory from several hubs in different parts of a company (managed by different organizations). This one "superhub" would allows executives instant insight into infrastructure integrity.

While demonstrating my prototype, an executive liked the idea of having data at her fingertips so much, she asked, can we put our Windows servers into CFEngine?

I said sure, but CFEngine inventory on Windows is not as detailed as it is for UNIX and Linux. The next question naturally then is how detailed is it?

To answer, I spun up a Windows Server 2012 VM in the Joyent public cloud (the Joyent UI is a delight to use, BTW, and I had my VM up in less than a minute) and bootstrapped it to a CFEngine hub in the same cloud. While I was able to pull policy immediately, the hub couldn't connect to the Windows server on port 5308 to collect reports until I went into the Windows Firewall with Advanced Security control panel and opened up port 5308. (Rackspace.com has a [decent write-up](https://support.rackspace.com/how-to/managing-the-windows-server-2012-firewall/).)

Here is what you get out of the box in the way of inventory.

| Name | Value |
| --- | --- |
| Windows roles | WinServer |
| System version | BOCHS - 1 |
| Host name | ownerco-18v4p42 |
| Hardware addresses | 90:b8:d0:52:7c:09, 90:b8:d0:b5:c7:94 |
| System manufacturer | Joyent |
| Disk free (%) on main drive (C:) | 69 |
| BIOS version | Bochs |
| Architecture | x86\_64 |
| OS type | windows |
| IPv4 addresses | 10.112.186.4, 165.225.131.21 |
| OS kernel | Windows Server 2012 |
| CFEngine ID | SHA=1f6666e1e88b05a4c7a98604ffa429bc452dc209a22e78072abd2d6eccb5170c |
| System serial number | 720f2caa |
| BIOS vendor | Bochs |
| CFEngine version | 3.7.4 |
| Server class | windows |
| Uptime minutes | 46 |
| OS | Windows Server 2012 |

The basics are there – hostname, OS version, disk utilization, network addresses. And, just like the UNIX/Linux inventory, the Windows inventory is extensible.

And just for fun, here is a screenshot showing the CFEngine processes running on Windows (the first three in the “ps” output).

![CFE on Windows screenshot](https://verticalsysadmin.com/wp-content/uploads/2016/10/image001.png?w=272&h=300)

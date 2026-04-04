---
title: "Introducing Infrastructure Inventory with CFEngine Enterprise"
date: 2016-10-05
author: "Aleksey Tsalolikhin"
---

Setting up involves [spinning up a hub](https://cfengine.com/learn/installing-cfengine-enterprise-25-free-policyserver/) and [installing lightweight agents](https://cfengine.com/learn/installing-cfengine-enterprise-25-free-hosts-clients/) on hosts, then running a bootstrap command. The system automatically discovers hostname, address, OS version, disk utilization, installed packages, etc. The agent refreshes inventory every 5–10 minutes.

Reporting UI capabilities: building charts and graphs, applying filters, custom report builder. Inventory is extensible via arbitrary external shell script or binary. Supports exporting to PDFs and CSVs.

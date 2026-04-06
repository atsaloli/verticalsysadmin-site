---
title: "Introducing Infrastructure Inventory with CFEngine Enterprise"
date: 2016-10-05
---

CFEngine Enterprise makes it absurdly easy to track deployed servers. All you have to do is [spin up a hub](https://cfengine.com/learn/installing-cfengine-enterprise-25-free-policyserver/), [install the lightweight agent](https://cfengine.com/learn/installing-cfengine-enterprise-25-free-hosts-clients/) on each host, and run `cf-agent --bootstrap <hub>` to setup a trust relationship between hub and hosts. (If you need any help setting this up, let me know.)

The agent will discover information about each host (hostname, address, OS version, disk utilization, packages installed, etc.) and the hub will collect and aggregate this data, so you can see at a glance things like, my OS inventory is 5% RHEL 4, 10% RHEL 5, 84% RHEL 6, and 1% RHEL 7.

The neat thing, because the agent is lightweight, CFEngine is able to refresh this inventory every 5-10 minutes, so when you go into the Reporting UI, the data is completely up to date -- even if you are provisioning hosts dynamically (scaling to meet demand, for example), the Reporting Portal will stay up to date.

CFEngine Enterprise has a great Reporting UI which can build charts and graphs on the fly (under Inventory Report in the Reports tab), you can add filters, and it has a custom report builder.

Plus the inventory is extensible -- you can run an arbitrary external shell script or binary (e.g. from third-party vendors) to harvest additional data about the environment. This new data gets picked up by the Enterprise Hub along with the built-in inventory.

The Reporting Portal can export PDFs and CSVs as well, so you can make pretty pie graphs and slides for corporate meetings if you're lucky enough to be involved in such! :)

You can see screenshots of the Reporting Portal in my [blog post](https://cfengine.com/company/blog-detail/infrastructure-management-at-scale-an-overview-of-cfengine-enterprise/) on cfengine.com.

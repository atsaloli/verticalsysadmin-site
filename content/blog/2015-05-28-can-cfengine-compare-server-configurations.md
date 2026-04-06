---
title: "Can CFEngine compare server configurations?"
date: 2015-05-28
---

One question I often hear sysadmins ask who are just getting into configuration management is, can CFEngine can report on configuration drift between servers? As in, take a server "A" and baseline it, and compare it to server "B", and make a report telling where things are different.

Comparing existing servers is the hard way to go about getting consistency.

I have a story about how I got into configuration management.

Back in 2000, I was working at EarthLink, about 5 million users. We had 8 mid-range Sun servers (a third of a rack each) handling relay of outgoing email. We noticed one of the servers had 35% better performance than the average, and a couple of servers had 10-20% worse. The rest were +/- 5% or so.

Naturally we wanted to configure all the servers like the leader.

I tried to analyze their configuration to find the magic sauce on the leader. The longer I looked (with ssh "for" loops), the more differences I found: sendmail version, sendmail config settings, OS version, patch sets, kernel tunables. Every server was unique, even though we had a build procedure. NOTHING was consistent.

We ended up moving to exim and consolidating to 6 servers with better performance but that's another story.

But that's when I realized there had to be a better way and started looking into configuration management; and that's when I found CFEngine.

There are a lot of configuration details on a server. Every file is potentially a configuration detail. Every line in every file. Every package. It takes live judgement to decide which configuration details are important and those are the ones you want to manage.

The CFEngine Way is to model the desired configuration in policy; CFEngine will converge your infrastructure to that configuration.

You do have to analyze your configuration to identify what's important to manage. You have to pick out the senior configuration details in a sea of detail. In our case (back to EarthLink), the exact version of sendmail wasn't important -- what turned out to be important was using exim instead. There is no substitute for live intelligence. It is an essential component of the man/machine hybrid modern civilization is shaping up to be.

Speaking of configuration differences, recently I've been enjoying the reporting features of CFEngine Enterprise (free for up to 25 nodes) at scale. You tag the configuration aspect you care about, and the hub polls the servers to inventory them and then summarizes and graphs the results. Upgrading to a new configuration across a fleet of servers, I see at a glance the upgrade was successful in 99%, but 1% require special attention and I can drill down and see the hosts that are in the 1%. This helps me get to 100%. No more unique snowflakes - not where it counts.

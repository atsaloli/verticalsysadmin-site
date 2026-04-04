---
title: "Can CFEngine Compare Server Configurations?"
date: 2015-05-28
author: "Aleksey Tsalolikhin"
---

Addresses whether CFEngine can report configuration drift by comparing a baseline server to others.

"Comparing existing servers is the hard way to go about getting consistency." Personal anecdote from 2000 at EarthLink: faced performance variations across eight mail relay servers despite having a build procedure. After extensive analysis, found numerous differences but no clear cause for the performance gap — which ultimately led to exploring CFEngine.

**Key insight:** "The CFEngine Way is to model the desired configuration in policy; CFEngine will converge your infrastructure to that configuration." Use CFEngine Enterprise's reporting to monitor compliance and identify non-compliant systems efficiently.

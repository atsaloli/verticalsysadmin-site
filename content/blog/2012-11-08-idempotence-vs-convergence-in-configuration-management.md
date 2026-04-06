---
title: "Idempotence vs Convergence in Configuration Management"
date: 2012-11-08
---

Diego Zamboni, author of "Learning CFEngine 3", [commented](http://chester.ozblogistan.com.au/2012/06/27/a-not-sobrief-aside-on-reigning-in-chaos#comment-1371) on [A not-so-brief aside on reigning in chaos](http://chester.id.au/2012/06/27/a-not-sobrief-aside-on-reigning-in-chaos/). His comment includes the clearest explanation of idempotence vs convergence I've ever seen:

> About idempotence vs convergence: as you rightly point out, they are not the same, and there are very important differences. Idempotence is an operation that leaves the system unmodified if it's already in the desired state, whereas convergence is the property of a system of not making unnecessary changes (nor operations). The end result may be the same, but CFEngine emphasizes convergence over idempotence, and has A LOT of built-in logic to automatically avoid performing unnecessary operations.

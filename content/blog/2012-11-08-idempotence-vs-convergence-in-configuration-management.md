---
title: "Idempotence vs Convergence in Configuration Management"
date: 2012-11-08
author: "Aleksey Tsalolikhin"
---

Cites Diego Zamboni (author of "Learning CFEngine 3") in a [blog post on reigning in chaos](http://chester.id.au/2012/06/27/a-not-sobrief-aside-on-reigning-in-chaos/):

> "Idempotence is an operation that leaves the system unmodified if already in the desired state, whereas convergence is the property of a system of not making unnecessary changes."

**Key distinction:** Idempotence focuses on individual operation behavior — repeated execution causes no additional changes. Convergence emphasizes system-level efficiency — avoiding unnecessary operations altogether.

CFEngine prioritizes convergence over idempotence, incorporating built-in logic to automatically prevent superfluous operations.

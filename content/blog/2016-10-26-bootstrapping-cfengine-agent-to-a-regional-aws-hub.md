---
title: "Bootstrapping CFEngine Agent to a Regional AWS Hub"
date: 2016-10-26
author: "Aleksey Tsalolikhin"
---

DevOps engineer Joaquin Menchaca provided this one-liner for determining an AWS region from within a VM:

```
AWS_REGION=$(curl -s http://169.254.169.254/latest/meta-data/placement/availability-zone | sed -e 's/[a-z]$//')
```

It queries instance metadata to identify which AWS region the VM is in. Useful when bootstrapping Kubernetes VMs to connect to the appropriate regional CFEngine hub — so each instance communicates with its nearest local hub.

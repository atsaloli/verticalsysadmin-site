---
title: "Dumping RPM Metadata"
date: 2016-07-11
author: "Aleksey Tsalolikhin"
---

Needed to identify which RPM metadata field stores the "el6" value visible in package version output. One-liner to dump all available RPM metadata fields:

```bash
rpm -q kernel-2.6.32-504.el6.x86_64 --queryformat "$(for f in `rpm --querytags`; do echo \n $f = %{${f}} ' ' ; done )"
```

The "RELEASE" field contains the relevant "504.el6" value, along with derived fields like EVR, NEVR, NEVRA, and NVR.

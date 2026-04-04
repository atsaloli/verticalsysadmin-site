---
title: "Identifying Critical Unpatched Vulnerabilities on a Red Hat System"
date: 2016-05-31
author: "Aleksey Tsalolikhin"
---

Working notes for identifying critical unpatched vulnerabilities on RHEL 6.

Install the yum-security plugin to list available security updates with associated CVEs and severity ratings:

```bash
yum update-info list cves available
```

To determine which unpatched CVEs have [CVSS](https://www.first.org/cvss) scores exceeding 7 (critical threshold): CVSS-scored CVEs are available from the [National Vulnerability Database](https://nvd.nist.gov/download.cfm) via XML feeds. NIST suggests a one-time import of all main XML vulnerability feeds, then regular updates with modified feeds.

The [Red Hat ratings system](https://access.redhat.com/security/updates/classification) provides additional severity context for RHEL-specific packages.

Demonstrates converting 2015 vulnerability data from XML to CSV using the [xml2 package](http://www.ofb.net/~egnor/xml2/) (sudo apt install xml2). Matching CVSS scores to the CVEs returned by yum-security is "left as an exercise for the reader."

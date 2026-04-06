---
title: "Identifying critical unpatched vulnerabilities on a Red Hat system"
date: 2016-05-31
---

These are some working notes for identifying critical unpatched vulnerabilities on a Red Hat Enterprise Linux system (version 6).

If you install yum-security plugin, you can list security updates available and which CVEs they relate to, as well as their severity according to [Red Hat ratings system](https://access.redhat.com/security/updates/classification):

`yum update-info list cves available`

Identifying which unpatched CVEs (as returned by the yum-security plugin) are Critical according to [CVSS (Common Vulnerability Scoring System)](https://www.first.org/cvss), with score > 7:

Scored CVEs are available from [National Vulnerability Database](https://nvd.nist.gov/download.cfm) through a set of XML feeds. The NIST web site says:

> A common way to use the feeds is to perform a one-time import of all of the main XML vulnerability feeds and then use the "modified" feeds to keep up-to-date.

The "xml2" package converts from XML to various formats. I started by converting the 2015 XML to CSV:

`$ xml2 < nvdcve-2.0-2015.xml > nvdcve-2.0-2015.flat $ 2csv entry vuln:cve-id vuln:cvss/cvss:base_metrics/cvss:score vuln:summary < nvdcve-2.0-2015.flat > nvdcve-2.0-2015.csv $`

Next step: lookup the CVSS scores for CVEs returned by yum-security, is left as an exercise for the reader.

Notes: - [xml2 home](http://www.ofb.net/~egnor/xml2/) - "xml2" is available through `sudo apt install xml2` on Ubuntu

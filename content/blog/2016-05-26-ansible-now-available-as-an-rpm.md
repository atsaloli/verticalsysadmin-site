---
title: "Ansible Now Available as an RPM"
date: 2016-05-26
author: "Aleksey Tsalolikhin"
---

Ansible is now available through the EPEL (Extra Packages for Enterprise Linux) repository as an RPM. The RPM handles dependency management automatically — no need to manually configure Python packages.

"The RPM provides Ansible version 2.0.2.0 which includes a number of bug fixes including a security one (CVE-2016-3096)."

Installing Ansible pulls in 14 total packages: PyYAML, libyaml, sshpass, and Python libraries (Babel, Crypto, httplib2, Jinja2, Keyczar, Paramiko, others). Total download: ~6.9 MB; installed size: ~33 MB.

"This is a lot easier to handle than fiddling with Python's package manager of the day."

---
title: "Ansible now available as an RPM"
date: 2016-05-26
---

Ansible is now available as an RPM from the EPEL repo. It pulls in all the dependencies needed by Ansible (Python libraries, libyaml and sshpass). The RPM provides Ansible version 2.0.2.0 which includes a number of bug fixes including a security one (CVE-2016-3096). This is a lot easier to handle than fiddling with Python's package manager of the day.

```
$ sudo yum install ansible
...
=============================================================================================================
Package                         Arch                 Version                       Repository          Size
=============================================================================================================
Installing:
ansible                         noarch               2.0.2.0-1.el6                 epel               2.9 M
Installing for dependencies:
PyYAML                          x86_64               3.10-3.1.el6                  base               157 k
libyaml                         x86_64               0.1.3-4.el6_6                 base                52 k
python-babel                    noarch               0.9.4-5.1.el6                 base               1.4 M
python-crypto                   x86_64               2.0.1-22.el6                  base               159 k
python-crypto2.6                x86_64               2.6.1-2.el6                   epel               513 k
python-httplib2                 noarch               0.7.7-1.el6                   epel                70 k
python-jinja2-26                noarch               2.6-3.el6                     epel               527 k
python-keyczar                  noarch               0.71c-1.el6                   epel               219 k
python-paramiko                 noarch               1.7.5-2.1.el6                 base               728 k
python-pyasn1                   noarch               0.0.12a-1.el6                 base                70 k
python-simplejson               x86_64               2.0.9-3.1.el6                 base               126 k
python-six                      noarch               1.9.0-2.el6                   base                28 k
sshpass                         x86_64               1.05-1.el6                    epel                19 k

Transaction Summary
=============================================================================================================
Install      14 Package(s)

Total download size: 6.9 M
Installed size: 33 M
Is this ok [y/N]:
```

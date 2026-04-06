---
title: "Bootstrapping CFEngine agent to a regional (AWS) hub"
date: 2016-10-26
---

Hat tip to my DevOps buddy Joaquin Menchaca for this one-liner to find out what AWS region your VM is in:

`AWS_REGION=$(curl -s http://169.254.169.254/latest/meta-data/placement/availability-zone | sed -e 's/[a-z]$//')`

I am going to use it to bootstrap my Kubernetes VMs to the right CFEngine hub for their AWS region (i.e., to the local hub).

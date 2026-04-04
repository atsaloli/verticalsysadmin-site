---
title: "Setting up a Postgres Sandbox"
date: 2016-11-13
author: "Aleksey Tsalolikhin"
tags: ["centos", "postgres", "postgresql", "vagrant", "virtual-box", "yum"]
---

Demonstrates creating a reproducible PostgreSQL development environment using Vagrant and VirtualBox.

## Steps

1. Install Vagrant and VirtualBox
2. Choose a base image (puppetlabs/centos-6.6-64-nocm)
3. Create a directory and initialize Vagrant
4. Download PostgreSQL 9.3 repository packages via wget, store RPMs in /vagrant/packages for persistence
5. Modify the Vagrantfile to automate database initialization
6. Destroy and recreate the VM to verify reproducibility

The automation script initializes PostgreSQL, creates a vagrant user with appropriate permissions, and enables the service. Users can then access PostgreSQL via psql. The approach allows repeating "destroy VM, bring it up, and start psql" as often as needed for a clean slate.

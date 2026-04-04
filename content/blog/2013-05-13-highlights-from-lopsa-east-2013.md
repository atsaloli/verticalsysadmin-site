---
title: "Highlights from LOPSA East 2013 Configuration Management Workflows Panel"
date: 2013-05-13
author: "Aleksey Tsalolikhin"
---

Key recommendations from the panel:

**Syntax Highlighting & Validation:** Use syntax highlighters to catch errors early. "Color highlighting lets you save time and trouble by catching errors early in the development process."

**Version Control Integration:** Pre-commit hooks to validate syntax. Jenkins for syntax-checking new commits. knife-spork from Etsy as a workflow solution for teams managing shared Chef repositories.

**Code Review:** Gerrit recommended as a Git-based web interface for code review.

**Testing:** Vagrant for testing configuration code; supports Ansible, Chef, CFEngine, Puppet, Shell provisioners. Use SSDs for faster VM startup. Jenkins for automated deployment.

**Testing strategies:** Unit testing (chefspec, rspec), integration testing (test-kitchen), user acceptance testing via canary deployments. cucumber-nagios for describing system behavior in natural language while generating Nagios-compatible output.

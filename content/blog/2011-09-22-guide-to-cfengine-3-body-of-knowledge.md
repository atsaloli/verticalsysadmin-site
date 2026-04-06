---
title: "Guide to CFEngine 3 Body of Knowledge"
date: 2011-09-22
---

Purpose: There is a lot to know about CFEngine, which can make it hard for people new to the subject.  The purpose of this guide is to lay out the resources available to CFEngine students and to orient them to this body of knowledge to speed their journey into practical system automation with CFEngine 3.

The guide is based largely on the materials of cfengine.com with full gratitude to Mark Burgess for continuously raising the bar in the field of system administration.

Comments welcome, please email me.

### Getting Started

- [CFEngine Quickstart](http://cfengine.com/manuals/cf3-quickstart.html "CFEngine Quickstart"): a Quick Start Guide.  Build and install from source; or install a package.  Then either set up CFEngine to run from cron; or start learning by running individual examples.
- [CFEngine 3 Concept Guide](http://cfengine.com/manuals/cf3-conceptguide.html "CFEngine 3 Concept Guide"): an abbreviated version of the CFEngine tutorial.  Topics include: Introduction - System automation; The components of CFEngine; Bodies and bundles; A simple crash course in concepts; Knowledge Management.

### Core Documentation

- [Glossary of Terms](http://www.cfengine.com/manuals/cf3-glossary.html "CFEngine Glossary")
- [Tutorial](http://www.cfengine.com/manuals/cf3-tutorial.html "Tutorial"): Covers the following topics:
    - [System automation](http://www.cfengine.com/manuals/cf3-tutorial.html#System-automation)
    - [The components of CFEngine](http://www.cfengine.com/manuals/cf3-tutorial.html#The-components-of-CFEngine)
    - [Bodies and bundles](http://www.cfengine.com/manuals/cf3-tutorial.html#Bodies-and-bundles)
    - [First promises](http://www.cfengine.com/manuals/cf3-tutorial.html#First-promises)
    - [A simple crash course in concepts](http://www.cfengine.com/manuals/cf3-tutorial.html#A-simple-crash-course-in-concepts)
    - [Using CFEngine as a front-end for cron](http://www.cfengine.com/manuals/cf3-tutorial.html#Using-CFEngine-as-a-front_002dend-for-cron)
    - [Network services](http://www.cfengine.com/manuals/cf3-tutorial.html#Network-services)
    - [Knowledge Management](http://www.cfengine.com/manuals/cf3-tutorial.html#Knowledge-Management)
- [CFEngine 3 Best Practices](http://www.cfengine.com/manuals/cf3-bestpractice.html "CFEngine 3 Best Practices"):  A guide to CFEngine 3 best practices.
    - [Policy Style Guide](http://www.cfengine.com/manuals/cf3-bestpractice.html#Policy-Style-Guide)
    - [Policy Dos and Don'ts](http://www.cfengine.com/manuals/cf3-bestpractice.html#Policy-Dos-and-Don_0027ts)
    - [Common Workflows](http://www.cfengine.com/manuals/cf3-bestpractice.html#Common-Workflows)
    - [Quality Assurance around CFEngine](http://www.cfengine.com/manuals/cf3-bestpractice.html#Quality-Assurance-around-CFEngine)
- [Troubleshooting](http://www.cfengine.com/pages/troubleshoot "Troubleshooting"): A guide to debugging and reporting errors.  The three common types of problems and how to handle them: CFEngine appears to hang; segmentation fault; memory leak.  Common misunderstandings: CFEngine does not always work - only sometimes; I am seeing multiple cf-agents in the process table, building up.
- [CFEngine Solutions](http://www.cfengine.com/manuals/cf3-solutions.html "CFEngine Solutions"): a Solutions Guide.  Basic examples (copying files, restarting processes, etc.).   High level solutions (adding users, setting up clusters, etc.).  Lots of low level examples (reading from a TCP socket, setting up a PXE boot server, etc.).  VERY USEFUL IN LEARNING CFENGINE.
- [Reference Manual](http://www.cfengine.com/manuals/cf3-reference.html "Reference Manual"):  Everything about CFEngine.  Auto-generated from the source code.   You'll likely spend most of your time in the [Bundles for agent](http://www.cfengine.com/manuals/cf3-reference.html#Bundles-for-agent "Bundles for agent") section.  INDISPENSABLE IN USING CFENGINE.
- [Syntax](http://www.cfengine.com/syntax): A companion to the Reference Manual, the syntax guide details all the parts of the CFEngine language and how they relate to each other.  A must read for aspiring CFEngine gurus.

### Learning CFEngine

- [Mark Burgess's Introduction to CFEngine 3](http://www.cfengine.com/inside/videos/): four videos comprising Mark's day class on CFEngine (find them at the top of the linked Training page):
    1. Introduction and motivation
    2. Understanding patterns and knowledge
    3. Client-Server basics
    4. Recap and the CFEngine landscape
- [CFEngine 3 Practical Examples](http://www.verticalsysadmin.com/cfengine/cfengine_examples.tar): A collection of practical examples to help learn CFEngine 3.  Use "ls -1" to display them in order (they are arranged from basic to more advanced).
- [CFEngine 3 Cookbook](http://watson-wilson.ca/cfengine/): A growing collection of practical examples well explained.  Neil's writing helped many sysadmins start with CFEngine 2 and 3.

### CFEngine Policy Source Code Libraries

- [CFEngine Community Open Promise-Body Library](http://cfengine.com/manuals/CfengineStdLibrary.html "COPBL") a.k.a. COPBL, a.k.a. cfengine\_stdlib.cf).  Please read the [purpose of the COPBL](http://cfengine.com/manuals/CfengineStdLibrary.html#The-Purpose-Of-This-Handbook "The Purpose of the COPBL")
- [Modular Bundles](http://source.cfengine.com/browse/copbl/trunk/ModularBundles/ "ModularBundles"): intended as a library of CFengine promise bundles. Has not been updated in over a year.
- [Orion Cloud Pack](http://source.cfengine.com/browse/copbl/trunk/OrionCloudServices/): another library of CFEngine promise bundles.  Configure more than 20 popular services.  (Intended to be used on Amazon EC2 but could work in lots of environments.)  Has not been updated in 9 months.  Also: [demo video](http://www.cfengine.com/demos/Orion) and [documentation](http://www.cfengine.com/manuals/OrionCloudPack.pdf).
- [Index of Third-party Shared Policies](http://www.verticalsysadmin.com/cfengine/shared-configs-index.html): CFEngine users have shared some policies outside the above libraries.
- [CFEngine 3 Practical Examples](http://www.verticalsysadmin.com/cfengine/cfengine_examples.tar): See "Learning CFEngine" above.
- [CFEngine 3 Cookbook](http://watson-wilson.ca/cfengine/): See "Learning CFEngine" above.

### Special Topics

- There is a large (and growing) number of guides on various topics: devops, file editing, adopting CFEngine, etc.  Check [Special Topics](http://cfengine.com/special_topics) for the full list.

### Enterprise Edition

- [Nova Quick Start Guide](http://www.cfengine.com/manuals/Cfengine_Nova_Quick_Start_Guide.pdf "Nova Quick Start Guide"): helps you install Nova and gives an overview of the beautiful admin GUI (the "Mission Portal").
- [CFEngine Nova Technical Supplement](http://www.cfengine.com/manuals/cfnova.html "CFEngine Nova Technical Supplement"): details Nova installation, admin GUI, and Nova capabilities:
    - Business integration
    - Monitoring extensions
    - Database control
    - File ACLs
    - Server extensions
    - Environments and workflows
    - Virtualization
    - Content-Driven Policies (Community Edition can do this too)
    - Windows-specific features

### Demo Videos

Video presentations demonstrating key capabilities of CFEngine Community and Enterprise editions.  The below content is straight from www.cfengine.com:

 

| [![CFEngine and Change Detection](http://www.cfengine.com/tl_files/cfengine/demos/thumb/thumbnail05.png)](http://www.cfengine.com/demos/Change_Detection) | [CFEngine and Change Detection](http://www.cfengine.com/demos/Change_Detection) - CFEngine offers extensive tripwire functionality. Combined with CFEngine auto-repair functionality you can ensure policy compliance on files and directories. In this video you will see how CFEngine detects file creation, file change and file deletion. Use CFEngine to secure your files and prevent unauthorized changes. With CFEngine you can keep track of all configuration changes and view them in detailed reports. |
| --- | --- |
| [![CFEngine and Apache Webserver](http://www.cfengine.com/tl_files/cfengine/demos/thumb/thumbnail06.png)](http://www.cfengine.com/demos/webserver) | [CFEngine and Apache Webserver](http://www.cfengine.com/demos/webserver) - This demo shows you how CFEngine can manage one Apache webserver to ensure server availability and uptime. Use policies to define how to manage your webservers, and CFEngine will make sure your webserver are compliant with your policies. Avoid any downtime due to misconfigured or accidentally deleted files. |
| [![CFEngine and Windows Registry](http://www.cfengine.com/tl_files/cfengine/demos/thumb/thumbnail07.png)](http://www.cfengine.com/demos/Windows_Registry_desktop) | [CFEngine and Windows Registry](http://www.cfengine.com/demos/Windows_Registry_desktop) - This demo shows you how CFEngine can manage the Windows registry. With CFEngine you can make sure the registry always stays compliant with your policies. Manage the whole registry or just specific keys and / or key-values. |
| [![CFEngine and PXE Boot](http://www.cfengine.com/tl_files/cfengine/demos/thumb/thumbnail08.png)](http://www.cfengine.com/demos/Cfengine_PXE_Boot) | [CFEngine and PXE Boot](http://www.cfengine.com/demos/Cfengine_PXE_Boot) - CFEngine manages your servers and networks of machines throughout the life-cycle. Use CFEngine during the build and deploy phase by creating PXE-boot servers controlled and deployed by CFEngine. Based on policies you can turn any server into whatever configuration setting you like, independent of operating system and required services. This demo will show how to create a CFEngine PXE-boot server and then install Redhat on a clean machine using CFEngine. PS: This demo has sound. |
| [![The Orion Cloud Pack](http://www.cfengine.com/tl_files/cfengine/demos/thumb/thumbnail09.png)](http://www.cfengine.com/demos/Orion) | [The Orion Cloud Pack](http://www.cfengine.com/demos/Orion) - Three Steps you need to bring reliability and efficiency to Managed Services running out of the Amazon Cloud. Set up and tear down machines as you like, and bring instant configuration and compliance, with self-healing to your business. |
| [![CFEngine Computer-Process Management](http://www.cfengine.com/tl_files/cfengine/demos/thumb/thumbnail12.png)](http://www.cfengine.com/demos/Process_Kill_Restart) | [CFEngine Computer-Process Management](http://www.cfengine.com/demos/Process_Kill_Restart) - Use CFEngine to manage your computer-processes. Use application-availability policies to ensure uptime at all times. CFEngine starts, deletes and/or restart processes, all according to your policies. In this video we will show how CFEngine restarts a broken Apache-server. The demo will show how CFEngine can kill a process, and how it automatically (the CFEngine Agent) restarts the same process. |
| [![CFEngine DNS Resolver](http://www.cfengine.com/tl_files/cfengine/demos/thumb/thumbnail13.png)](http://www.cfengine.com/demos/Cfengine_DNS_Resolver) | [CFEngine DNS Resolver](http://www.cfengine.com/demos/Cfengine_DNS_Resolver) - This clip shows how cfengine can deal with a very common issue in network configuration: setting up the name-server bindings. DNS configuration is sometimes done by DHCP, but statically configured servers can be maintained by CFEngine directly. We show how CFEngine repairs a damaged configuration file to ensure the correct settings. |

### Misc.

- [Command Reference](http://www.cfengine.com/manuals/cf-QuickRef3.html): a summary of command line options for each CFEngine component.

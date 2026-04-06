---
title: "Relative Origin of Cfengine, Puppet and Chef"
date: 2010-09-15
---

![Relative Origin of Cfengine, Chef and Puppet](http://verticalsysadmin.com/images/relative_origin_of_cfengine_chef_and_puppet.png)

In Cfengine, creator Mark Burgess pioneered the idea of using a configuration description language to describe desired state on heterogeneous Unix and Unix-like systems. This language included "classes" or built-in if/then tests to control when and where the configuration should apply.

In Cfengine 2, Mark introduced ideas of convergence to a desired state and self-healing (computer immunology).

Puppet was created by a power Cfengine 2 user Luke Kanies out of his dissatisfaction with Cfengine 2 and Mark's management of the project. Next generation tool after Cfengine 2, Puppet is graph-based and model-driven and has a very simple DSL language (designed to be simple, safe and human readable) and now a Ruby DSL (for additional power and flexibility). Puppet has a large and active community.

Chef rose out of the cloudy Ruby-on-Rails world. Chef was created by Adam Jacobs, a power Puppet user, out of dissatisfaction with Puppet’s non-deterministic (by default - it can be made deterministic) graph-based ordering. Sequence of execution in Chef is tightly ordered. The most exciting innovation in Chef is cloud provisioning capability (ability to instantiate cloud VM's, install and configure the OS, and install the application - all automatically).

Cfengine 3 is a complete rewrite of Cfengine 2 completely addressing the pain points of Cfengine 2 (such as baroqueness of language syntax) and moving the entire field forward. Mark greatly simplified the language and introduced Promise Theory, a way to think about configuration as promises to be in a desired state.

Cfengine 3 innovations are Knowledge Management (making the intention clear, documenting who cares about an aspect of configuration or what it effects, and enabling extensive sysadmin commenting that accompanies the configuration) and Business Integration (such as enabling auditing compliance or enabling ITIL processes).

Cfengine 3 also brings new capabilities such as database integration (control of database state) and native support for managing Windows registry state.

P.S. Be assured development and continued enhancement is ongoing in all three. This graph only tracks major version numbers. Puppet is continuing to make its own way.

---
title: "Highlights from LOPSA East 2013 Configuration Management Workflows panel"
date: 2013-05-13
---

# Use Syntax Highlighters

Highlighting syntax is a big time server. Color highlighting lets you save time and trouble by catching errors early in the development process.

Use a syntax plug-in for your editor!

# Revision control system hooks.  Code review.

You can set up a precommit hook to validate syntax before accepting code into your VCS repository; or you can use Jenkins to syntax-check new commits and move them to another branch if they validate.

knife-spork from Etsy is a workflow plugin from Etsy to allow multiple users to work on the same Chef repo/server without stepping on each other's toes. Spork integrates with graphite and IRC. Good for big teams! [https://github.com/jonlives/knife-spork](https://github.com/jonlives/knife-spork)

Gerrit is a Web-based code review system based on git. [https://code.google.com/p/gerrit/](https://code.google.com/p/gerrit/)

## Use Vagrant to test your code.

[http://vagrantup.com/](http://vagrantup.com/)

- Vagrant has provisioners for Ansible, Chef, CFEngine, Puppet and Shell.
- You do have block out or disable external dependencies (since Vagrant is encapsulated).
- SSDs pay for themselves. VMs come up much faster.
- Matt Barr keeps a local copy of CentOS DVD mounted to provide the full repo to his Vagrant VMs. He also deploys new code to VMs automatically.
- Sinatra is a web development framework for minimalists. You can use it to quickly build simulators of external web services inside your Vagrant environment.
- Jenkins can deploy your code into Vagrant VMs

# Testing

foodcritic, puppetlint and cf-promises check syntax. But how do you check the output (the modified system)? The answers are unit testing, integration testing and user acceptance testing.

Use Jenkins, TravisCI, etc.

rspec is a Ruby testing framework. You can write tests for your configuration in it.

[http://rspec.info/](http://rspec.info/)

For Chef, chefspec is an extension to rspec for unit-testing. Also, minitests and test-kitchen ([http://www.opscode.com/blog/2012/08/17/announcing-test-kitchen/](http://www.opscode.com/blog/2012/08/17/announcing-test-kitchen/) and [https://github.com/opscode/test-kitchen](https://github.com/opscode/test-kitchen))

For Puppet: serverspec + rspec do functional checks of remote systems.

## User acceptance testing

You can deploys to test VMs first (like Matt does).

You can deploy to "canary" servers (a limited production deploy, AKA "toe-in-the-water" deploy).

External monitoring can be done with traditional tools, such as Nagios.

cucumber-nagios lets you describe how a system should work in natural language, and outputs whether it does in the Nagios plugin format [http://www.cucumber-nagios.org/](http://www.cucumber-nagios.org/) [http://fooforge.com/2012/11/06/Analyzing-my-OSMC-2012-talk-on-BDI.html](http://fooforge.com/2012/11/06/Analyzing-my-OSMC-2012-talk-on-BDI.html)

---
title: "Setting up a Postgres Sandbox"
date: 2016-11-13
tags: 
  - "centos"
  - "postgres"
  - "postgresql"
  - "vagrant"
  - "virtual-box"
  - "yum"
---

I'm a fan of disposable sandboxes using Vagrant and VirtualBox.

I've been using [Postgres](https://en.wikipedia.org/wiki/PostgreSQL) on the job for nearly a year, and a while back I decided it was time to have a dedicated Postgres instance on my personal computer, on a virtual machine, just to play around with.

I'm using a Mac, but the steps below should work without change for Windows or Linux. Let me know in the comments if you run into any problems following these steps!

### How to set up a _reproducible_ Postgres sandbox inside a disposable VM

1. If you haven't done so already, install [Vagrant](https://www.vagrantup.com) and [VirtualBox](https://www.virtualbox.org).
    
2. [Choose a Vagrant base image.](https://atlas.hashicorp.com/boxes/search) For my own purposes I chose the vanilla base box `puppetlabs/centos-6.6-64-nocm` (which comes from Puppet Labs but doesn't have Puppet installed.)
    
    There are [official images for CentOS](https://atlas.hashicorp.com/centos) and [official images for Ubuntu](https://atlas.hashicorp.com/ubuntu) as well, in addition to the vast range of user-contributed images. (The official CentOS image doesn't come with VirtualBox guest additions installed, though, so folder syncing won't work out of the box.)
    
    You don't have to _do_ anything with your choice just yet, just choose one.
    
3. Open your terminal or command line environment.
    
4. Create a dedicated directory for this particular Vagrant environment to live in, and change directories to that directory. (I personally use `~/term/vagrant/centos-6`.)
    
    ```
    mkdir -p ~/term/vagrant/centos-6
    cd !$
    ```
    
    (`!$` makes use of a Bash feature called "[History Expansion](http://unix.stackexchange.com/a/275061/135943)." It expands to the last portion of the last command executed, in this case `~/term/vagrant/centos-6`.)
    
5. Initialize the Vagrant environment, specifying the base image (box) you chose in step 2.
    
    ```
    vagrant init puppetlabs/centos-6.6-64-nocm
    ```
    
    You can run `ls` and observe that a `Vagrantfile` has been created:
    
    ```
    $ ls
    Vagrantfile
    ```
    
6. Bring up the Vagrant environment, which (this first time) will also download the base image you chose earlier.
    
    ```
    vagrant up
    ```
    
    This may take a little while. Wait for it.
    
7. Log in to the Vagrant virtual machine you've created.
    
    ```
    vagrant ssh
    ```
    
8. If you want a particular version of Postgres, choose the version of the [Postgres _yum repository_ package](https://yum.postgresql.org/repopackages.php) from which you can download the Postgres package itself. (I chose Postgres 9.3.) Right click and choose "copy link." Then, inside your Vagrant VM, run the following command, replacing the URL with the one you've just copied.
    
    ```
    wget https://download.postgresql.org/pub/repos/yum/9.3/redhat/rhel-6-x86_64/pgdg-redhat93-9.3-3.noarch.rpm
    ```
    
9. Install the package you've just downloaded.
    
    ```
    sudo yum install -y ./pgdg-redhat93-9.3-3.noarch.rpm
    ```
    
10. Create a "packages" directory inside `/vagrant`, to store the Postgres packages _outside_ the VM, where they will be saved when the VM is destroyed. Change to this directory.
     
     ```
     mkdir /vagrant/packages
     cd !$
     ```
     
11. Download the Postgres packages (ignoring the versions present in the default repositories).
     
     ```
     yumdownloader --resolve --disablerepo=* --enablerepo=pgdg* postgresql*-server
     ```
     
12. Exit, and verify that the "packages" directory shows up on your host with three RPMs inside.
     
     ```
     exit
     ls packages
     ```
     
13. Modify the `Vagrantfile` to include the shell commands to initialize Postgres.
     
     Change the commented out lines (near the bottom of the file) that read as follows:
     
     ```
       # config.vm.provision "shell", inline: <<-SHELL
       #   apt-get update
       #   apt-get install -y apache2
       # SHELL
     ```
     
     And replace them with:
     
     ```
       config.vm.provision "shell", inline: <<-SHELL
         yum install -C -y /vagrant/packages/postgresql*.rpm
         service postgresql-9.3 initdb
         service postgresql-9.3 start
         chkconfig postgresql-9.3 on
         sudo -i -u postgres createuser -d -e -E -I -r -s vagrant
         sudo -i -u vagrant createdb -e
       SHELL
     ```
     
     Save the changes.
     
14. Destroy your vagrant environment.
     
     ```
     vagrant destroy
     ```
     
15. Bring it up again and log in.
     
     ```
     vagrant up && vagrant ssh
     ```
     
16. Run `psql`. You're in.
     
     ```
     [vagrant@localhost ~]$ psql
     psql (9.3.15)
     Type "help" for help.
     
     vagrant=# q
     [vagrant@localhost ~]$
     ```
     

* * *

Now you can play around, do whatever you like inside the Postgres instance, and just repeat the last three steps (destroy VM, bring it up, and start psql) as often as you need to. :)

Did these instructions help? Did you have any trouble? Any suggestions? Let me know in the comments.

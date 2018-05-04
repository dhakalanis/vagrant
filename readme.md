# Welcome to the Vagrant README wiki page!
------------------------------------------------------------------------
This wiki mainly covers instruction for installing Vagrant, VirtualBox, Working Directory for Vagrant, VagrantFile etc.

The main goal of this wiki page is to help setup VirtualBox, Vagrant environment, create VMs(VirtualMachines), ssh to VMs.
------------------------------------------------------------------------
### My Environments (Local Machine Overview):
All the steps and instructions are performed on my below local machine.
* Model Name:	MacBook Pro
* System Version:	OS X EL Capitan (10.11.6)
* Kernel Version:	Darwin 15.6.0
* Processor Name:	Intel Core i5
* Processor Speed:	2.7 GHz
* Number of Processors:	1
* Total Number of Cores:	2
* L2 Cache (per Core):	256 KB
* L3 Cache:	3 MB
* Memory:	8 GB

```
DhakalComputerID:Vagrant DhakalUserID$ uname -a
Darwin DhakalComputerID 15.6.0 Darwin Kernel Version 15.6.0: Mon Aug 29 20:21:34 PDT 2016; root:xnu-3248.60.11~1/RELEASE_X86_64 x86_64
DhakalComputerID:Vagrant DhakalUserID$
```
------------------------------------------------------------------------
### Download and Install Vagrant and Virtual Box:
Download below on your machine (In my case i used MAC OS X)
* Virtual Box: https://www.virtualbox.org/wiki/Downloads
* Vagrant: https://www.vagrantup.com/downloads.html 

#### VBOX:

![](https://github.com/dhakalanis/vagrant/blob/master/Images/VBOX_1.png)
------------------------------------------------------------------------

![](https://github.com/dhakalanis/vagrant/blob/master/Images/VBOX_2.png)
------------------------------------------------------------------------

![](https://github.com/dhakalanis/vagrant/blob/master/Images/VBOX_3.png)
------------------------------------------------------------------------

![](https://github.com/dhakalanis/vagrant/blob/master/Images/VBOX_4.png)
------------------------------------------------------------------------

![](https://github.com/dhakalanis/vagrant/blob/master/Images/VBOX_5.png)
------------------------------------------------------------------------

![](https://github.com/dhakalanis/vagrant/blob/master/Images/VBOX_6.png)
------------------------------------------------------------------------

![](https://github.com/dhakalanis/vagrant/blob/master/Images/Vagrant_1.png)
------------------------------------------------------------------------

![](https://github.com/dhakalanis/vagrant/blob/master/Images/Vagrant_2.png)
------------------------------------------------------------------------

![](https://github.com/dhakalanis/vagrant/blob/master/Images/Vagrant_3.png)
------------------------------------------------------------------------

![](https://github.com/dhakalanis/vagrant/blob/master/Images/Vagrant_4.png)
------------------------------------------------------------------------


I'm using below versions. Below command is after installation:
* VBOX:
```
DhakalComputerID:Vagrant DhakalUserID$ vboxmanage --version
5.2.10r122088
DhakalComputerID:Vagrant DhakalUserID$ 
```
* Vagrant:

```
DhakalComputerID:Vagrant DhakalUserID$ vagrant --version
Vagrant 2.0.4
DhakalComputerID:Vagrant DhakalUserID$
```

Helpful CLI:
* https://www.virtualbox.org/manual/ch08.html
* https://www.vagrantup.com/docs/cli/

------------------------------------------------------------------------

### Working Directory and VagrantFile.
* Create a directory where you can initialize vagrant.
* Perform “vagrant init” which will create “Vagrantfile”. This is the default file which needs editing so that we can configure it. This is created where you performed “vagrant init”
Command: vagrant init
This initializes the current directory to be a Vagrant environment by creating an initial Vagrantfile if one does not already exist.

My working Directory is: 
```
DhakalComputerID:Vagrant DhakalUserID$ pwd
/Users/DhakalUserID/Documents/OneDrive - DhakalCompanyName/Work_Related/Common/Vagrant
DhakalComputerID:Vagrant DhakalUserID$ ls | grep Vagrantfile
Vagrantfile
```
Once Vagrantfile is created, please go ahead and edit the file based on your requirements. I have edited the file so that it can create 2 VMs (dhakal and dhakalweb).
Content of the VagrantFile (after edited):
```

# -*- mode: ruby -*-
# vi: set ft=ruby :

# All Vagrant configuration is done below. The "2" in Vagrant.configure
# configures the configuration version (we support older styles for
# backwards compatibility). Please don't change it unless you know what
# you're doing.
Vagrant.configure("2") do |config|

  config.vm.define "dhakal" do |dhakal|
    dhakal.vm.box = "ubuntu/trusty64"
    # GOt it from https://app.vagrantup.com/boxes/search
    dhakal.vm.hostname = "dhakal"
    #Inside the OS hostname.
    dhakal.vm.network "private_network", ip: "192.168.33.10"
  end

  config.vm.define "dhakalweb" do |dhakalweb|
    dhakalweb.vm.box = "ubuntu/trusty64"
    # Got it from https://app.vagrantup.com/boxes/search
    dhakalweb.vm.hostname = "dhakalweb"
    #Inside the OS hostname.
    dhakalweb.vm.network "private_network", ip: "192.168.33.20"
  end

end
```
------------------------------------------------------------------------
### Vagrant CLI (Vagrant Up, Status, SSH)

* Command: vagrant up

Once Vagrantfile has been edited, please perform "vagrant up". This command creates and configures guest machines according to your Vagrantfile.
This is the single most important command in Vagrant, since it is how any Vagrant machine is created. Anyone using Vagrant must use this command on a day-to-day basis.

* Command: vagrant status

This will tell you the state of the machines Vagrant is managing.
It is quite easy, especially once you get comfortable with Vagrant, to forget whether your Vagrant machine is 
running, suspended, not created, etc. This command tells you the state of the underlying guest machine.

* Command: vagrant ssh

This will SSH into a running Vagrant machine and give you access to a shell.
If a -- (two hyphens) are found on the command line, any arguments after this are passed directly into the ssh executable. This allows you to pass any arbitrary commands to do things such as reverse tunneling down into the ssh program.
NOTE :: Default vagrant username / pwd: vagrant/vagrant)

Examples of the vagrant cli on my environment based on my Vagrantfile.
```
DhakalComputerID:Vagrant DhakalUserID$ vagrant status
Current machine states:

dhakal                    running (virtualbox)
dhakalweb                 running (virtualbox)

This environment represents multiple VMs. The VMs are all listed
above with their current state. For more information about a specific
VM, run `vagrant status NAME`.

DhakalComputerID:Vagrant DhakalUserID$ vboxmanage list vms
"Vagrant_dhakal_1525207147017_85220" {a39c6ac3-3283-451a-a555-7bea8e03a6ba}
"Vagrant_dhakalweb_1525207446201_32265" {032e22e5-c9bc-4aa0-a07c-bcaa50b45989}
DhakalComputerID:Vagrant DhakalUserID$

```

![](https://github.com/dhakalanis/vagrant/blob/master/Images/VBOX_7.png)
------------------------------------------------------------------------

```
DhakalComputerName:Vagrant DhakalUserID$ vagrant ssh dhakal
Welcome to Ubuntu 14.04.5 LTS (GNU/Linux 3.13.0-145-generic x86_64)

 * Documentation:  https://help.ubuntu.com/

  System information as of Tue May  1 20:39:39 UTC 2018

  System load:  0.96              Processes:           83
  Usage of /:   3.6% of 39.34GB   Users logged in:     0
  Memory usage: 27%               IP address for eth0: 10.0.2.15
  Swap usage:   0%

  Graph this data and manage this system at:
    https://landscape.canonical.com/

  Get cloud support with Ubuntu Advantage Cloud Guest:
    http://www.ubuntu.com/business/services/cloud

0 packages can be updated.
0 updates are security updates.

New release '16.04.4 LTS' available.
Run 'do-release-upgrade' to upgrade to it.


vagrant@dhakal:~$ uname -a
Linux dhakal 3.13.0-145-generic #194-Ubuntu SMP Thu Apr 5 15:20:44 UTC 2018 x86_64 x86_64 x86_64 GNU/Linux
vagrant@dhakal:~$ 
```

------------------------------------------------------------------------

NOTE: If you want to pursue further with Ansible installation, please refer to https://github.com/dhakalanis/ansible or (directly to https://github.com/dhakalanis/ansible/blob/master/readme.md)

------------------------------------------------------------------------

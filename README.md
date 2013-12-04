BOX
===

Spin up a development VM quickly and easily from the command line. 

This is essentially a wrapper for virtualbox and vagrant, but it automates the setup a little and makes it possible to spin up a VM for a project with one or two commands. 

I really use this as a base for other projects that need customized VMs. It's just a python script, so it can be quickly modified and installed on virtually any unixy system.


Requirements
------------

* Python
* A linux/unixy system
* Virtualbox
* Vagrant 1.2+


Installation
------------

To install `box`, download the repo and run the `install` script.

For instance, if you download and unzip the files in `~/Downloads/box`, you'd do this:

    $ cd ~/Downloads/box
    $ ./install

If it asks you for a password, supply it.

Once the `install` script runs, the command `box` will be available on your system.


Creating a VM
-------------

To create a VM, make a folder to house your VM and navigate into it:

    $ mkdir ~/ubuntu-vm 
    $ cd ~/ubuntu-vm

Then run the `box init` command:

    $ box init

That's it. Now you can use the VM.


Using the VM
------------

Use `box up` to boot up the VM:

    $ box up

Use `down` to shut it down:

    $ box down

And use `ssh` to SSH into it.


Provisioning the VM
-------------------

When you run `box init` in a folder, a hidden folder called `.devbox` is created there. The config files for your VM are stored there.

If you look in `.devbox/config/bash`, you'll see a file called `provision`. That's just a bash script, and the VM runs it (as root) the first time the VM boots up.

If you want to install anything special on your VM, you can put it in this file. If you've already booted the VM and want to reapply this script to the VM, run:

    $ box provision

Deleting the VM
---------------

If you want to delete the VM, use the `destroy` command:

    $ box destroy

The hidden `.devbox` folder is not deleted though. You need to delete it yoursel if you want it removed.



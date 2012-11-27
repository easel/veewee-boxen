This repository contains veewee templates which can be used to build [Vagrant base boxes](http://vagrantup.com/docs/boxes.html).  It will install the latest VirtualBox Guest Additions and create a user account called 'vagrant', with the password set to 'vagrant'. It was originally based on https://github.com/avtar/fedora-16-i386.git but has been renamed to better reflect there are multiple templates included.

## Installation

These instructions assume that you are using Ruby 1.9.3 with RVM.

    $ gem install vagrant
    $ gem install veewee

Clone this repository.

    $ git clone https://github.com/easel/veewee-boxen

Begin building the box.  The installer will prompt you during the file system partitioning phase, asking for confirmation before it erases the virtual drive.  Once you agree to that the rest of the installation will proceed unattended.  This should take a couple of minutes depending on the speed of your internet connection.  The virtual machine will restart itself twice.  The last time it does so, it will run the postinstall.sh script which install the Guest Additions among other necessary changes.

    $ vagrant basebox build 'Fedora-16-i386'

If all went well, you should see a Fedora login prompt.  You can now export the base box.

    $ vagrant basebox export Fedora-16-i386

You should now have a 'Fedora-16-i386.box' file.  This will need to be imported before Vagrant can begin using it.

    $ vagrant box add 'Fedora-16-i386' 'Fedora-16-i386.box'

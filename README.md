mono-aspnetvnext Vagrant box
============================

*The GitHub repository hosts the Vagrantfile used to create the box at [https://vagrantcloud.com/akoeplinger/mono-aspnetvnext](https://vagrantcloud.com/akoeplinger/mono-aspnetvnext). Do __not__ clone the repository, just follow the [instructions](#setup-vagrant-box) below*

The box contains everything needed to play with ASP.NET vNext projects on Mono.

By using Vagrant, you can run a VM with everything set up correctly without messing with your Windows, Linux or Mac OSX host.

# Requirements

* **VirtualBox**: [https://www.virtualbox.org/wiki/Downloads](https://www.virtualbox.org/wiki/Downloads)
* **Vagrant**: [http://www.vagrantup.com/downloads.html](http://www.vagrantup.com/downloads.html)

# Setup Vagrant box
To use the box and run the included "Hello World" sample, follow these steps:

1. Run `vagrant up` to download the Vagrant box and boot the VM
2. Run `vagrant ssh` to connect to the VM
3. `cd helloworld/`
4. Run `kvm upgrade` to install mono lasted version
5. `cd src/helloworldweb`
6. Run `kpm restore` to restore the necessary packages
7. Start the test web server by running `k web`

The "Hello World" web application should now be running, access it by browsing to http://localhost:5000.

The folder containing the Vagrantfile is automatically mapped to the VM path `/vagrant`. This is a simple way to share your own projects with the VM.

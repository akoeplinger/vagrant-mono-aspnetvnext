# -*- mode: ruby -*-
# vi: set ft=ruby :

# Vagrantfile API/syntax version. Don't touch unless you know what you're doing!
VAGRANTFILE_API_VERSION = "2"

Vagrant.configure(VAGRANTFILE_API_VERSION) do |config|
  # All Vagrant configuration is done here. The most common configuration
  # options are documented and commented below. For a complete reference,
  # please see the online documentation at vagrantup.com.

  config.vm.box = "chef/ubuntu-14.04"

  # Create a forwarded port mapping which allows access to a specific port
  # within the machine from a port on the host machine. In the example below,
  # accessing "localhost:8080" will access port 8080 on the guest machine.
  config.vm.network "forwarded_port", guest: 8080, host: 8080

$script = <<SCRIPT

sudo apt-get -y install curl unzip git-core build-essential autoconf libtool gettext libgdiplus libgtk2.0-0 xsltproc

cd /tmp
git clone --depth=1 https://github.com/mono/mono
cd mono
./autogen.sh --prefix=/usr --with-mcs-docs=no
make get-monolite-latest
make
sudo make install
sudo rm -r /tmp/mono

mozroots --import --sync
curl https://raw.githubusercontent.com/graemechristie/Home/KvmShellImplementation/kvmsetup.sh | sh && source ~/.kre/kvm/kvm.sh && kvm upgrade

git clone https://github.com/davidfowl/HelloWorldVNext ~/helloworld

cd ~/helloworld
kpm restore

SCRIPT

  config.vm.provision "shell", inline: $script, privileged: false

end

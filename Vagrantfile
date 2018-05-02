# Please refer to https://github.com/dhakalanis/vagrant/wiki for “Working Directory and VagrantFile.”
# ——————————————————————————————————————————————————————————————————————————————————————————————————————
# ——————————————————————————————————————————————————————————————————————————————————————————————————————

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

# -*- mode: ruby -*-
# vi: set ft=ruby :

# Grab the name of the default interface
$default_network_interface = `ip route | awk '/^default/ {printf "%s", $5; exit 0}'`

# All Vagrant configuration is done below. The "2" in Vagrant.configure
# configures the configuration version (we support older styles for
# backwards compatibility). Please don't change it unless you know what
# you're doing.
Vagrant.configure("2") do |config|
  config.vm.box = "hashicorp/bionic64"

  config.vm.network "public_network", bridge: "#$default_network_interface"

  config.vm.provider "virtualbox" do |vb|
  #   vb.memory = "1024"
  end

  config.vm.provision "ansible" do |a|
    a.verbose = "v"
    a.playbook = "master_playbook.yaml"
  end
end

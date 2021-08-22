# -*- mode: ruby -*-
# vi: set ft=ruby :

# All Vagrant configuration is done below. The "2" in Vagrant.configure
# configures the configuration version (we support older styles for
# backwards compatibility). Please don't change it unless you know what
# you're doing.
Vagrant.configure("2") do |config|
  config.vm.box = "geerlingguy/ubuntu2004"
  
  if Vagrant.has_plugin?("vagrant-vbguest")
    config.vbguest.auto_update = false
  end
  config.vm.provider :virtualbox do |v|
    v.memory = 10521
    v.cpus = 4
    v.customize ["modifyvm", :id, "--natdnshostresolver1", "on"]
    v.customize ["modifyvm", :id, "--ioapic", "on"]
  end
  
  config.vm.define :control do |control|
    control.vm.hostname = "baothi"
    control.vm.box = "geerlingguy/ubuntu2004"
    control.vm.box_check_update = false
    control.vm.synced_folder "./rails/", "/home/vagrant/rails/"
  end
  # config.vm.network :forwarded_port, guest: 3000, host: 3000
  # http://192.168.1.18:3000/
  config.vm.network "public_network", bridge: "en1: Wi-Fi (AirPort)"

  config.vm.provision "shell", inline: <<-SHELL
    sudo apt-get -y install kernel-devel
    sudo apt-get -y upgrade
    sudo apt-get update
    sudo adduser vagrant vboxsf
    sudo apt-get install -y curl
    sudo apt install unzip
    sudo sysctl -w net.ipv6.conf.all.disable_ipv6=1
    sudo sysctl -w net.ipv6.conf.default.disable_ipv6=1
  SHELL
end





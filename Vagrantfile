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
    v.memory = 1521
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
    curl -sL https://deb.nodesource.com/setup_12.x | sudo -E bash -
    curl -sS https://dl.yarnpkg.com/debian/pubkey.gpg | sudo apt-key add -
    echo "deb https://dl.yarnpkg.com/debian/ stable main" | sudo tee /etc/apt/sources.list.d/yarn.list
    sudo apt-get -y update
    sudo apt-get -y install git-core zlib1g-dev build-essential libssl-dev libreadline-dev libyaml-dev libsqlite3-dev sqlite3 libxml2-dev libxslt1-dev libcurl4-openssl-dev software-properties-common libffi-dev nodejs yarn
    git config --global user.name "baothi"
    git config --global user.email "baothi246@gmail.com"
    ssh-keygen -t rsa -b 4096 -C "baothi246@gmail.com"
    git clone https://github.com/rbenv/rbenv.git ~/.rbenv
    echo 'export PATH="$HOME/.rbenv/bin:$PATH"' >> ~/.bashrc
    echo 'eval "$(rbenv init -)"' >> ~/.bashrc
    exec $SHELL

    git clone https://github.com/rbenv/ruby-build.git ~/.rbenv/plugins/ruby-build
    echo 'export PATH="$HOME/.rbenv/plugins/ruby-build/bin:$PATH"' >> ~/.bashrc
    exec $SHELL
  SHELL
end





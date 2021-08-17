# -*- mode: ruby -*-
# vi: set ft=ruby :

# All Vagrant configuration is done below. The "2" in Vagrant.configure
# configures the configuration version (we support older styles for
# backwards compatibility). Please don't change it unless you know what
# you're doing.
Vagrant.configure("2") do |config|
  # The most common configuration options are documented and commented below.
  # For a complete reference, please see the online documentation at
  # https://docs.vagrantup.com.

  # Every Vagrant development environment requires a box. You can search for
  # boxes at https://vagrantcloud.com/search.
  config.vm.box = "geerlingguy/ubuntu2004"
  
  config.vm.provider :virtualbox do |vb|
    # Display the VirtualBox GUI when booting the machine
    # vb.gui = true
  
    # Customize the amount of memory on the VM:
    vb.cpus = 4
    vb.memory = "16024"
    vb.customize ["modifyvm", :id, "--natdnshostresolver1", "on"]
    vb.customize ["modifyvm", :id, "--ioapic", "on"]
  end


  config.vm.define :control do |control|
    control.vm.hostname = "baothi"
    control.vm.box = "geerlingguy/ubuntu2004"
    control.vm.box_check_update = false
    # control.vm.synced_folder "data/", "/tmp/data",
    #   create: true, id: "data",
    #   owner: "root", "group": "root"
  end
  # Disable automatic box update checking. If you disable this, then
  # boxes will only be checked for updates when the user runs
  # `vagrant box outdated`. This is not recommended.
  # config.vm.box_check_update = false

  # Create a forwarded port mapping which allows access to a specific port
  # within the machine from a port on the host machine. In the example below,
  # accessing "localhost:8080" will access port 80 on the guest machine.
  # NOTE: This will enable public access to the opened port
  # config.vm.network "forwarded_port", guest: 80, host: 8080

  # Create a forwarded port mapping which allows access to a specific port
  # within the machine from a port on the host machine and only allow access
  # via 127.0.0.1 to disable public access
  # config.vm.network "forwarded_port", guest: 80, host: 8080, host_ip: "127.0.0.1"
  config.vm.network :forwarded_port, guest: 3000, host: 3000
  # config.vm.provision :shell, :inline => $as_root, :privileged => true
  # config.vm.provision :shell, :inline => $as_vagrant, :privileged => false
  # Create a private network, which allows host-only access to the machine
  # using a specific IP.
  config.vm.network "private_network", ip: "192.168.33.10"

  # Create a public network, which generally matched to bridged network.
  # Bridged networks make the machine appear as another physical device on
  # your network.
  # config.vm.network "public_network"

  # Share an additional folder to the guest VM. The first argument is
  # the path on the host to the actual folder. The second argument is
  # the path on the guest to mount the folder. And the optional third
  # argument is a set of non-required options.
  # config.vm.synced_folder "../data", "/vagrant_data"

  # Provider-specific configuration so you can fine-tune various
  # backing providers for Vagrant. These expose provider-specific options.
  # Example for VirtualBox:
  #
  
  
  #
  # View the documentation for the provider you are using for more
  # information on available options.

  # Enable provisioning with a shell script. Additional provisioners such as
  # Ansible, Chef, Docker, Puppet and Salt are also available. Please see the
  # documentation for more information about their specific syntax and use.
  config.vm.provision "shell", inline: <<-SHELL
    sudo apt install curl
    curl -sL https://deb.nodesource.com/setup_12.x | sudo -E bash -
    curl -sS https://dl.yarnpkg.com/debian/pubkey.gpg | sudo apt-key add -
    echo "deb https://dl.yarnpkg.com/debian/ stable main" | sudo tee /etc/apt/sources.list.d/yarn.list
    sudo apt-get update
    sudo apt-get -y install git-core zlib1g-dev build-essential libssl-dev libreadline-dev libyaml-dev libsqlite3-dev sqlite3 libxml2-dev libxslt1-dev libcurl4-openssl-dev software-properties-common libffi-dev nodejs yarn
    # git clone https://github.com/rbenv/rbenv.git ~/.rbenv
    # echo 'export PATH="$HOME/.rbenv/bin:$PATH"' >> ~/.bashrc
    # echo 'eval "$(rbenv init -)"' >> ~/.bashrc
    # exec $SHELL
    # git clone https://github.com/rbenv/ruby-build.git ~/.rbenv/plugins/ruby-build
    # echo 'export PATH="$HOME/.rbenv/plugins/ruby-build/bin:$PATH"' >> ~/.bashrc
    # exec $SHELL
    # rbenv install 3.0.1
    # rbenv global 3.0.1
    # ruby -v
    # gem install bundler
    # git config --global color.ui true
    # git config --global user.name "baothi"
    # git config --global user.email "baothi246@gmail.com"
    # ssh-keygen -t rsa -b 4096 -C "baothi246@gmail.com"
    # gem install rails -v 6.1.3.2
    # rbenv rehash
    # rails -v
  SHELL
end

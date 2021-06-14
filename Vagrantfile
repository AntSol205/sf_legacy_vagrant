# -*- mode: ruby -*-
# vi: set ft=ruby :


Vagrant.configure("2") do |config|

  config.vm.box = "ubuntu/bionic64"

  # NOTE: This will enable public access to the opened port
  config.vm.network "forwarded_port", guest: 5432, host: 5432
#  config.vm.network "forwarded_port", guest: 80, host: 80

# config.vm.network "forwarded_port", guest: 5432, host: 5432, host_ip: "127.0.0.1"

# config.vm.network "private_network", ip: "192.168.33.10"

# config.vm.synced_folder "../data", "/vagrant_data"

  #
  config.vm.provider "virtualbox" do |vb|
  #   # Display the VirtualBox GUI when booting the machine
  #  vb.gui = true
  #
  #   # Customize the amount of memory on the VM:
    vb.memory = "2048"
   # vb.customize ["modifyvm", :id, "--natdnshostresolver1", "on"]
   # vb.customize ["modifyvm", :id, "--natdnsproxy1", "on"]
  end
  config.vm.define "postgresql-8.4" do |t|
  end
  config.vm.provider "virtualbox" do |v|
  v.name = "postgresql-8.4"
  end
  #
  config.vm.provision "shell", inline: <<-SHELL
  #ufw disable
  sh -c 'echo "deb http://apt.postgresql.org/pub/repos/apt $(lsb_release -cs)-pgdg main" > /etc/apt/sources.list.d/pgdg.list'
  wget --quiet -O - https://www.postgresql.org/media/keys/ACCC4CF8.asc | sudo apt-key add -
  apt-get update
  apt-get install -y postgresql-8.4
 
 SHELL
end

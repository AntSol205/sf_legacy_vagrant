# -*- mode: ruby -*-
# vi: set ft=ruby :


Vagrant.configure("2") do |config|

  config.vm.box = "ubuntu/bionic64"

  config.vm.network "forwarded_port", guest: 5432, host: 5432
  #
  config.vm.provider "virtualbox" do |vb|
  #
    vb.memory = "2048"
   						
  end
  #
  config.vm.define "postgresql-8.4" do |t|
  end
  #
  config.vm.provider "virtualbox" do |v|
  v.name = "postgresql-8.4"
  end
  #
  config.vm.provision "shell", inline: <<-SHELL
  sh -c 'echo "deb http://apt.postgresql.org/pub/repos/apt $(lsb_release -cs)-pgdg main" > /etc/apt/sources.list.d/pgdg.list'
  wget --quiet -O - https://www.postgresql.org/media/keys/ACCC4CF8.asc | sudo apt-key add -
  apt-get update
  apt-get install -y postgresql-8.4
 
 SHELL
end

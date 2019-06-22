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
  config.vm.box = "debian/stretch64"

  
  config.vm.network "private_network", ip: "192.168.111.111"


  config.vm.provision "shell", inline: <<-SHELL
    apt-get remove docker docker-engine docker.io containerd runc

    apt-get update

    apt-get install \
    apt-transport-https \
    ca-certificates \
    curl \
    gnupg2 \
    software-properties-common -y

    curl -fsSL https://download.docker.com/linux/debian/gpg | apt-key add -

    add-apt-repository \
   "deb [arch=amd64] https://download.docker.com/linux/debian \
   $(lsb_release -cs) \
   stable"

   apt-get update

   apt-get install docker-ce docker-ce-cli containerd.io -y

  curl -L "https://github.com/docker/compose/releases/download/1.24.0/docker-compose-$(uname -s)-$(uname -m)" -o /usr/local/bin/docker-compose

  chmod +x /usr/local/bin/docker-compose

  usermod -a -G docker vagrant

  apt-get clean 

  apt-get autoclean

  SHELL
end

# -*- mode: ruby -*-
# vi: set ft=ruby :

# Deploy VMs using Ubuntu/Trusty64 and enable hostmanager support for hostname population
Vagrant.configure(2) do |config|
  config.vm.box = "ubuntu/trusty64"
  config.hostmanager.enabled = true
  config.hostmanager.manage_host = true
  config.hostmanager.ignore_private_ip = false
  config.hostmanager.include_offline = true
  # Deploy the VMs and setup and IPv4 (eth1) and IPv6 (eth2) address
  config.vm.define "etcd-01" do |config|
    config.vm.provider "virtualbox" do |vb|
      vb.name = "etcd-01"
    config.vm.hostname = "etcd-01"
    end
    config.vm.network "private_network", ip: "192.168.20.10"
    config.vm.network "private_network", ip: "2001:db8:cafe:14::a"
  end

  config.vm.define "manager-01" do |config|
    config.vm.provider "virtualbox" do |vb|
      vb.name = "manager-01"
    config.vm.hostname = "manager-01"
    end
    config.vm.network "private_network", ip: "192.168.20.11"
    config.vm.network "private_network", ip: "2001:db8:cafe:14::b"
  end

  config.vm.define "node-01" do |config|
    config.vm.provider "virtualbox" do |vb|
      vb.name = "node-01"
    config.vm.hostname = "node-01"
    end
    config.vm.network "private_network", ip: "192.168.20.12"
    config.vm.network "private_network", ip: "2001:db8:cafe:14::c"
  end

  config.vm.define "node-02" do |config|
    config.vm.provider "virtualbox" do |vb|
      vb.name = "node-02"
    config.vm.hostname = "node-02"
    end
    config.vm.network "private_network", ip: "192.168.20.13"
    config.vm.network "private_network", ip: "2001:db8:cafe:14::d"
  end

  config.vm.provider "virtualbox" do |vb|
    vb.gui = false
    vb.memory = "1024"
    vb.cpus = 1
    vb.customize ["modifyvm", :id, "--vram", "8"]
  end
  # Run an update and install the experimental branch of Docker
  config.vm.provision "shell", inline: <<-SHELL
    sudo apt-key adv --keyserver hkp://p80.pool.sks-keyservers.net:80 --recv-keys 58118E89F3A912897C070ADBF76221572C52609D
    sudo apt-get update
    sudo apt-get -y install linux-image-extra-$(uname -r)
    sudo curl -sSL https://experimental.docker.com/ | sh
    usermod -a -G docker vagrant
  SHELL
end

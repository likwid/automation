# -*- mode: ruby -*-
# vi: set ft=ruby :

# Vagrantfile API/syntax version. Don't touch unless you know what you're doing!
VAGRANTFILE_API_VERSION = "2"

Vagrant.configure(VAGRANTFILE_API_VERSION) do |config|

  config.vm.define "server" do |server|
    server.vm.box = "ubuntu/trusty64"
    server.vm.hostname = "apt-server"
    server.vm.network "private_network", ip: "192.168.50.5"

    server.vm.provider "virtualbox" do |vb|
      vb.memory = 2048
      vb.cpus = 2
      vb.customize ["modifyvm", :id, "--natdnshostresolver1", "on"]
    end

    server.vm.provision "ansible" do |ansible|
      ansible.playbook = "ansible/provision.yml"
    end

  end

  config.vm.define "client" do |client|
    client.vm.box = "ubuntu/trusty64"
    client.vm.hostname = "apt-client"
    client.vm.network "private_network", ip: "192.168.50.10"

    client.vm.provider "virtualbox" do |vb|
      vb.memory = 2048
      vb.cpus = 2
      vb.customize ["modifyvm", :id, "--natdnshostresolver1", "on"]
    end

    client.vm.provision "ansible" do |ansible|
      ansible.playbook = "ansible/provision.yml"
    end
  end

end

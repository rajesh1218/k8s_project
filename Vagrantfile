# -*- mode: ruby -*-
# vi: set ft=ruby :

BOX_IMAGE = "ubuntu/focal64"
MEMORY = "2048"
CPU = "2"

Vagrant.configure("2") do |config|
  config.vm.define "kmaster" do |subconfig|
    subconfig.vm.box = BOX_IMAGE
    subconfig.vm.hostname = "kmaster"
	subconfig.vm.network :private_network, ip: "192.168.56.101"
	subconfig.vm.provider :virtualbox do |vb|
          vb.customize ["modifyvm", :id, "--memory", MEMORY]
          vb.customize ["modifyvm", :id, "--cpus", CPU]
	end
  end
  config.vm.define "kworker1" do |subconfig|
    subconfig.vm.box = BOX_IMAGE
    subconfig.vm.hostname = "kworker1"
	subconfig.vm.network :private_network, ip: "192.168.56.102"
	subconfig.vm.provider :virtualbox do |vb|
          vb.customize ["modifyvm", :id, "--memory", MEMORY]
          vb.customize ["modifyvm", :id, "--cpus", CPU]
	end
  end
  config.vm.define "kworker2" do |subconfig|
    subconfig.vm.box = BOX_IMAGE
    subconfig.vm.hostname = "kworker2"
	subconfig.vm.network :private_network, ip: "192.168.56.103"
	subconfig.vm.provider :virtualbox do |vb|
          vb.customize ["modifyvm", :id, "--memory", MEMORY]
          vb.customize ["modifyvm", :id, "--cpus", CPU]
	end
  end
  #Install some additional packages 
  config.vm.provision "shell", inline: <<-SHELL
	sudo su
	sed -i 's/PasswordAuthentication no/PasswordAuthentication yes/g' /etc/ssh/sshd_config    
    service sshd reload
	apt-get update
  SHELL
end
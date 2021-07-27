# -*- mode: ruby -*-
# vi: set ft=ruby :

# All Vagrant configuration is done below. The "2" in Vagrant.configure
# configures the configuration version (we support older styles for
# backwards compatibility). Please don't change it unless you know what
# you're doing.
Vagrant.configure("2") do |config|

  
  config.vm.define "ansible_master_1" do |ansible_master_1|
        config.vm.box = "bento/ubuntu-20.04"
        config.vm.provision "file", source: "./ansible_ssh_key.pub", destination: "/home/vagrant/.ssh/ansible_ssh_key.pub"
        config.vm.provision "file", source: "./ansible_ssh_key", destination: "/home/vagrant/.ssh/ansible_ssh_key"
	config.vm.network "private_network", ip: "172.16.28.90"
	config.vm.provision "shell", inline: <<-'SCRIPT'
		cat /home/vagrant/.ssh/ansible_ssh_key.pub >> /home/vagrant/.ssh/authorized_keys
		sed -i 's/#PasswordAuthentication yes/PasswordAuthentication no/' /etc/ssh/sshd_config
		apt-get -y install mc
	SCRIPT
  end
end

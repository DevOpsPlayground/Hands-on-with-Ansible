# -*- mode: ruby -*-
# vi: set ft=ruby :

$script = <<SCRIPT
sudo apt-get install tree
sudo apt-get install software-properties-common
sudo apt-add-repository ppa:ansible/ansible
sudo apt-get update
sudo apt-get install ansible -y
sudo mkdir /ansible
sudo cp /etc/ansible/ansible.cfg /ansible
sudo touch /ansible/hosts
sudo sed -i 's?#inventory      = /etc/ansible/hosts?inventory = /ansible/hosts?g' /ansible/ansible.cfg
SCRIPT

Vagrant.configure("2") do |config|

  config.vm.define :control do |control|
    control.vm.box = "ubuntu/trusty64"
    control.vm.hostname = "control"
    control.vm.network :private_network, type: "dhcp"
    control.vm.provision "shell", inline: $script
  end

  config.vm.define :database do |database|
    database.vm.box = "ubuntu/trusty64"
    database.vm.network :private_network, type: "dhcp"
    database.vm.hostname = "database"
  end
end

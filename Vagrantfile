# -*- mode: ruby -*-
# vi: set ft=ruby :
Vagrant.configure("2") do |config|
  config.vm.box = "debian/stretch64"
  config.vm.network "private_network", type: "dhcp"
  config.vm.define "node0", primary: true do |n|
      n.vm.hostname = "node0"
  end
  config.vm.define "node1" do |n|
      n.vm.hostname = "node1"
  end
  config.vm.define "node2" do |n|
      n.vm.hostname = "node2"
  end

  config.vm.provision "shell",
      inline: "apt-get update && apt-get install -y python-minimal unzip"
  config.vm.provision "ansible" do |ansible|
    ansible.playbook = "provision.yml"
    ansible.become = true
    ansible.raw_arguments = ["--extra-vars", "ran_from_vagrant='true'"]
  end
end

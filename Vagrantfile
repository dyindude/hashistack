# -*- mode: ruby -*-
# vi: set ft=ruby :
Vagrant.configure("2") do |config|
  config.vm.box = "debian/stretch64"
  config.vm.network "public_network", :bridge => "eno2", :dev => "eno2"
  N=2
  (0..N).each do |i|
      config.vm.define "node#{i}" do |n|
          n.vm.hostname = "node#{i}"
          if i == N
              n.vm.provision "ansible" do |ansible|
                ansible.limit = 'all'
                ansible.playbook = "provision.yml"
                ansible.become = true
                ansible.galaxy_role_file = "requirements.yml"
                ansible.raw_arguments = ["--extra-vars", "ran_from_vagrant='true'"]
              end
              n.vm.provision "ansible" do |ansible|
                ansible.limit = 'node0'
                ansible.playbook = "vault-init.yml"
                ansible.become = true
                ansible.raw_arguments = ["--tags", "init", "--skip-tags", "untagged"]
              end
          end
      end
  end
end

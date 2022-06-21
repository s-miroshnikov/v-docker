# -*- mode: ruby -*-
# vi: set ft=ruby :

Vagrant.configure("2") do |config|
  (1..3).each do |i|
  config.vm.define "node-#{i}" do |node|
  config.vm.box = "bento/ubuntu-20.04"
  # Disable automatic box update checking. If you disable this, then
  # boxes will only be checked for updates when the user runs
  # `vagrant box outdated`. This is not recommended.
  config.vm.box_check_update = false
  node.vm.hostname = "v-docker-#{i}"
  
  # Share an additional folder to the guest VM. The first argument is
  # the path on the host to the actual folder. The second argument is
  # the path on the guest to mount the folder. And the optional third
  # argument is a set of non-required options.
  # config.vm.synced_folder "../data", "/vagrant_data"
   end
  end
  config.vm.provision "ansible_local" do |ansible|
   ansible.become = true  
   ansible.playbook = "docker-install.yml"
  end
end

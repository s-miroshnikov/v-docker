# -*- mode: ruby -*-
# vi: set ft=ruby :

Vagrant.configure("2") do |config|
  (1..3).each do |i|
  config.vm.define "node-#{i}" do |node|
  config.vm.box = "bento/ubuntu-20.04"
  config.vm.box_check_update = false
  node.vm.hostname = "v-docker-#{i}"
  node.trigger.after :up do |trigger|
    trigger.info = "Machine is up!"
    trigger.ruby do |env,machine|
      greetings = "hello there #{machine.id}!"
      puts greetings
  end
  end
  end
  end
  config.vm.provision "ansible_local" do |ansible|
   ansible.become = true  
   ansible.playbook = "docker-install.yml"
  end
end

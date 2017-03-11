# -*- mode: ruby -*-
# vi: set ft=ruby :

Vagrant.configure("2") do |config|
  N = 1
  (1..N).each do |machine_id|
    config.vm.box = "debian/wheezy64"
    config.vm.define "node#{machine_id}" do |machine|
      machine.vm.hostname = "node#{machine_id}"
      machine.vm.network "private_network", ip: "192.168.77.#{10+machine_id}"
      config.vm.provider "virtualbox" do |vb|
        vb.customize ["modifyvm", :id, "--memory", "2048"]
        vb.cpus = 2
        if machine_id == N
          machine.vm.provision :ansible do |ansible|
            ansible.limit = "all"
            ansible.playbook = "cassandra.yml"
            
          end
        end
      end
    end
  end
end

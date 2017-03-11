# -*- mode: ruby -*-
# vi: set ft=ruby :
# -*- mode: ruby -*-
# vi: set ft=ruby :

Vagrant.configure("2") do |config|
<<<<<<< HEAD
  # Base VM OS configuration.
  config.vm.box = "debian/wheezy64"
  config.vm.synced_folder '.', '/vagrant', disabled: true
  config.ssh.insert_key = false

  config.vm.provider :virtualbox do |v|
    v.memory = 256
    v.cpus = 1
  end

  # Define two VMs with static private IP addresses.
  boxes = [
    { :name => "node1", :ip => "192.168.77.11" },
    { :name => "node2", :ip => "192.168.77.12" },
    { :name => "node3", :ip => "192.168.77.13" }
  ]

  # Provision each of the VMs.
  boxes.each do |opts|
    config.vm.define opts[:name] do |config|
      config.vm.hostname = opts[:name]
      config.vm.network :private_network, ip: opts[:ip]

      # Provision both VMs using Ansible after the last VM is booted.
      if opts[:name] == "node3"
        config.vm.provision "ansible" do |ansible|
          ansible.playbook = "cassandra.yml"
          ansible.inventory_path = "envs/cassandra"
          ansible.limit = "all"
=======
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
>>>>>>> 8950ee256506efb7faeb1cd57f34fb6cc5b65d5e
        end
      end
    end
  end

end

# -*- mode: ruby -*-
# vi: set ft=ruby :

VAGRANTFILE_API_VERSION = '2'

Vagrant.configure(VAGRANTFILE_API_VERSION) do |config|
  config.ssh.insert_key = false
  config.vm.box_check_update = false
  config.vbguest.auto_update = false
  config.vm.box = "centos/7"
  ansible_inventory_dir = "provisioning/inventory"

  config.vm.provider :virtualbox do |vb|
    vb.customize [
      "modifyvm", :id,
      "--memory", 1024
    ]
    vb.customize [
      "modifyvm", :id,
      "--cpus", 1
    ]
  end

  config.vm.define "master01" do |master01|
    master01.vm.hostname = "master01.hautran.local"
    master01.vm.network :private_network, ip: "192.168.57.10"
  end

  config.vm.define "slave01" do |slave01|
    slave01.vm.hostname = "slave01.hautran.local"
    slave01.vm.network :private_network, ip: "192.168.57.11"
  end

  config.vm.define "slave02" do |slave02|
    slave02.vm.hostname = "slave02.hautran.local"
    slave02.vm.network :private_network, ip: "192.168.57.12"
  end

  # Install software dependencies
  #config.vm.provision "ansible" do |ansible|
  #  ansible.playbook = "provisioning/linux-essentials.yml"
  #  ansible.become = true
  #end

  # Install MongoDB replica set
  #config.vm.provision "ansible" do |ansible|
  #  ansible.playbook = "provisioning/mongodb-replica-set.yml"
  #  ansible.inventory_path = "#{ansible_inventory_dir}"
  #  ansible.limit = "all"
  #  ansible.become = true
  #end

  # Install Redis cluster
  #config.vm.provision "ansible" do |ansible|
  #  ansible.playbook = "provisioning/redis-ha.yml"
  #  ansible.inventory_path = "#{ansible_inventory_dir}"
  #  ansible.limit = "all"
  #  ansible.become = true
  #end

  # Install Percona MySQL
  config.vm.provision "ansible" do |ansible|
    ansible.playbook = "provisioning/setup-percona-mysql-gtid.yml"
    ansible.inventory_path = "#{ansible_inventory_dir}"
    ansible.limit = "all"
    ansible.become = true
  end

end

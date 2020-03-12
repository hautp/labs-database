# -*- mode: ruby -*-
# vi: set ft=ruby :

VAGRANTFILE_API_VERSION = '2'

Vagrant.configure(VAGRANTFILE_API_VERSION) do |config|
  config.ssh.insert_key = false
  config.vm.box_check_update = false
  config.vbguest.auto_update = false
  config.vm.box = "centos/7"

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

end

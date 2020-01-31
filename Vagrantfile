# -*- mode: ruby -*-
# vi: set ft=ruby :

ENV['VAGRANT_NO_PARALLEL'] = 'yes'

Vagrant.configure(2) do |config|

  config.vm.provision "shell", path: "bootstrap.sh"

#  # Master Server
#  config.vm.define "master" do |master|
#    master.vm.box = "centos/7"
#    master.vm.hostname = "master"
#    master.vm.network "private_network", ip: "172.42.42.100"
#    master.vm.provider "virtualbox" do |v|
#      v.name = "Master"
#      v.memory = 12288
#      v.cpus = 4
#      # Prevent VirtualBox from interfering with host audio stack
#      v.customize ["modifyvm", :id, "--audio", "none"]
#    end
#    master.vm.provision "shell", path: "bootstrap_master.sh"
#  end

  NodeCount = 3

  # Worker Nodes
  (1..NodeCount).each do |i|
    config.vm.define "server#{i}" do |workernode|
      workernode.vm.box = "centos/7"
      workernode.vm.hostname = "server#{i}"
      workernode.vm.network "private_network", ip: "172.42.42.10#{i}"
      workernode.vm.provider "virtualbox" do |v|
        v.name = "server#{i}"
        v.memory = 4096
        v.cpus = 4
        # Prevent VirtualBox from interfering with host audio stack
        v.customize ["modifyvm", :id, "--audio", "none"]
      end
    workernode.vm.provision "shell", path: "bootstrap.sh"
   end
  end

end


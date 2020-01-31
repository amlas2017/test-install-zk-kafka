#$script = <<-SCRIPT
#echo I am provisioning...
#apt install python-setuptools -y
#apt install -y git
#easy_install pip
#pip install ansible==2.8.4
#SCRIPT
 
servers=[
  {
    :hostname => "server1",
    :ip => "192.168.100.10",
    :box => "bento/ubuntu-18.04",
    :ram => 4096,
    :cpu => 8
  },
  {
    :hostname => "server2",
    :ip => "192.168.100.11",
    :box => "bento/ubuntu-18.04",
    :ram => 4096,
    :cpu => 4
  },
  {
    :hostname => "server3",
    :ip => "192.168.100.12",
    :box => "bento/ubuntu-18.04",
    :ram => 4096,
    :cpu => 4
  },
  
#{
#    :hostname => "client",
#    :ip => "192.168.100.9",
#    :box => "ubuntu/trusty64",
#    :ram => 512,
#    :cpu => 2
# }
]

Vagrant.configure(2) do |config|
  servers.each do |machine|
    config.vm.define machine[:hostname] do |node|
      node.vm.box = machine[:box]
      node.vm.hostname = machine[:hostname]
      node.vm.network "private_network", ip: machine[:ip]
      node.vm.provider "virtualbox" do |vb|
        vb.customize ["modifyvm", :id, "--memory", machine[:ram]]
        vb.customize ["modifyvm", :id, "--cpus", machine[:cpu]]
      end
 
#      if machine[:hostname] == "client"
#        config.vm.provision "ansible" do |ansible|
#         ansible.playbook = "deploy-swarm.yml"     # définir le playbook"
#            ansible.verbose = true
#        end
#       end
    end
  end
end

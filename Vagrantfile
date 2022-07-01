# -*- mode: ruby -*-

Vagrant.configure("2") do |config|

  config.vm.define "balancer" do |bal|
    bal.vm.box = "geerlingguy/debian10"
    bal.vm.network "private_network", ip: "192.168.56.17"
    bal.vm.provision "ansible" do |ansible|
      ansible.limit = "balancer"
      ansible.playbook = "playbook-balancer.yaml"
    end
  end

  N = 2
  (1..2).each do |id|
    config.vm.define "backend#{id}" do |be|
      be.vm.box = "geerlingguy/debian10"
      be.vm.network "private_network", ip: "192.168.56.#{id + 17}"
      if id == N
        be.vm.provision "ansible" do |ansible|
          ansible.limit = "all"
          ansible.playbook = "playbook-backend.yaml"
        end
      end
    end
  end

end

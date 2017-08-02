Vagrant.configure(2) do |config|
  config.vm.define "webserver" do |webserver|
    webserver.vm.box = "ubuntu/trusty64"
    webserver.vm.network "private_network", ip: "192.168.10.102"
    webserver.vm.hostname = "webserver"
  end
  config.vm.define "ansible" do |ansible|
    ansible.vm.box = "ubuntu/trusty64"
    ansible.vm.network "private_network", ip: "192.168.10.101"
    ansible.vm.hostname = "ansible"
  end
  config.vm.define "webserveransible" do |webserveransible|
    webserveransible.vm.box = "ubuntu/trusty64"
    webserveransible.vm.network "private_network", ip: "192.168.10.103"
    webserveransible.vm.hostname = "webserver-ansible"
    config.vm.provision "ansible_local" do |ansible|
      ansible.verbose = "vvv"
      ansible.playbook = "nginx.yml"
    end
  end
  config.vm.define "webserveransible1" do |webserveransible1|
    webserveransible1.vm.box = "ubuntu/trusty64"
    webserveransible1.vm.network "private_network", ip: "192.168.10.104"
    webserveransible1.vm.hostname = "webserver-ansible-not-local"
    config.vm.provision "ansible" do |ansible1|
      ansible1.playbook = "nginx.yml"
      ansible1.verbose = "vvv"
    end
  end
end

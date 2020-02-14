# -*- mode: ruby -*-
# vi: set ft=ruby :

Vagrant.configure("2") do |config|
  config.vm.define "app" do |app|
    app.vm.hostname = "app.explorium"
    app.vm.network "private_network", ip: "192.168.77.21"
    app.vm.box = "centos/7"

    app.vm.provider "virtualbox" do |v|
      v.memory = 512
      v.cpus = 1
    end

    app.vm.provision "ansible_local" do |ansible|
      ansible.playbook = "ansible/playbooks/app.yml"
      ansible.become = true
      ansible.galaxy_roles_path = "ansible/roles/"
    end
  end

  config.vm.define "registry" do |registry|
    registry.vm.hostname = "registry.explorium"
    registry.vm.network "private_network", ip: "192.168.77.22"
    registry.vm.box = "centos/7"

    registry.vm.provider "virtualbox" do |v|
      v.memory = 512
      v.cpus = 1
    end

    registry.vm.provision "ansible_local" do |ansible|
      ansible.playbook = "ansible/playbooks/registry.yml"
      ansible.become = true
      ansible.galaxy_roles_path = "ansible/roles/"
    end
  end

  config.vm.define "jenkins" do |jenkins|
    jenkins.vm.hostname = "jenkins.explorium"
    jenkins.vm.network "private_network", ip: "192.168.77.23"
    jenkins.vm.box = "centos/7"

    jenkins.vm.provider "virtualbox" do |v|
      v.memory = 2048
      v.cpus = 2
    end

    jenkins.vm.provision "ansible_local" do |ansible|
      ansible.playbook = "ansible/playbooks/jenkins.yml"
      ansible.become = true
      ansible.galaxy_roles_path = "ansible/roles/"
    end
  end
end

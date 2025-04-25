## VERSION A CREAR
# -*- mode: ruby -*-
# vi: set ft=ruby :

Vagrant.configure("2") do |config|
  # Configuración común para todos los nodos
  config.vm.box_check_update = false

  # Nodo Manager
  config.vm.define "manager" do |manager|
    manager.vm.box = "bento/rockylinux-9"
    manager.vm.hostname = "manager"
    manager.vm.network "private_network", ip: "192.168.33.10"
    manager.vm.provider "virtualbox" do |vb|
      vb.name = "manager"
      vb.memory = 3072 # 3GB
      vb.cpus = 2
    end
    manager.vm.provision "shell", inline: <<-SHELL
      sudo yum -y update
      sudo yum -y install python3 
      sudo dnf config-manager --add-repo https://download.docker.com/linux/centos/docker-ce.repo
      sudo dnf install docker-ce docker-ce-cli containerd.io
      sudo systemctl start docker
      sudo systemctl status docker
    SHELL
  end

  # Nodo1
  config.vm.define "nodo1" do |nodo1|
    nodo1.vm.box = "bento/rockylinux-9"
    nodo1.vm.hostname = "nodo1"
    nodo1.vm.network "private_network", ip: "192.168.33.11"
    nodo1.vm.provider "virtualbox" do |vb|
      vb.name = "nodo1"
      vb.memory = 2048 # 2GB
      vb.cpus = 1
    end
    nodo1.vm.provision "shell", inline: <<-SHELL
      sudo yum -y update
      sudo yum -y install python3
      sudo dnf config-manager --add-repo https://download.docker.com/linux/centos/docker-ce.repo
      sudo dnf install docker-ce docker-ce-cli containerd.io
      sudo systemctl start docker
      sudo systemctl status docker
    SHELL
  end

  # Nodo2
#  config.vm.define "nodo2" do |nodo2|
#    nodo2.vm.box = "bento/rockylinux-8"
#    nodo2.vm.hostname = "nodo2"
#    nodo2.vm.network "private_network", ip: "192.168.33.12"
#    nodo2.vm.provider "virtualbox" do |vb|
#      vb.name = "nodo2"
#      vb.memory = 2048 # 2GB
#      vb.cpus = 1
#    end
#    nodo2.vm.provision "shell", inline: <<-SHELL
#      sudo yum -y update
#      sudo yum -y install python3
#      sudo dnf config-manager --add-repo https://download.docker.com/linux/centos/docker-ce.repo
#      sudo dnf install docker-ce docker-ce-cli containerd.io
#      sudo systemctl start docker
#      sudo systemctl status docker
#    SHELL
#  end
end

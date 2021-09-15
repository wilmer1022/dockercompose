# -*- mode: ruby -*-
# vi: set ft=ruby :

Vagrant.configure("2") do |config|
	if Vagrant.has_plugin? "vagrant-vbguest"
		config.vbguest.no_install  = true
		config.vbguest.auto_update = false
		config.vbguest.no_remote   = true
	end
	config.vm.define :servidorUbuntu do |servidorUbuntu|
		servidorUbuntu.vm.box = "bento/ubuntu-20.04"
		servidorUbuntu.vm.network :private_network, ip: "192.168.100.3"
		servidorUbuntu.vm.hostname = "ftpdockerserver"
		servidorUbuntu.vm.provision "file", source: "docker-compose.yml", destination: "/home/vagrant/docker-compose.yml"
		servidorUbuntu.vm.provision "shell", path: "script_docker.sh"
		servidorUbuntu.vm.provider "virtualbox" do |v|
			v.name = "dockerUbuntuCompose"
			v.memory = 2048
			v.cpus = 2
		end
	end
end
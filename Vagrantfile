# -*- mode: ruby -*-
# vi: set ft=ruby :

unless Vagrant.has_plugin?("vagrant-docker-compose")
	raise 'Missing vagrant-docker-compose plugin! Make sure to install it by `vagrant plugin install vagrant-docker-compose`.'
end

Vagrant::configure("2") do | config |
	config.vm.synced_folder ".", "/vagrant", disabled: false
	config.vm.box = "ubuntu/xenial64"
	config.vm.hostname = "DockerBuildVM"

	config.vm.provider "virtualbox" do | v |
		v.cpus = 4
		v.memory = 4096
	end

	config.vm.provision "shell", run: "once", inline: <<-SHELL
		apt-get update
		sudo DEBIAN_FRONTEND=noninteractive apt-get upgrade -y -o Dpkg::Options::="--force-confdef" -o Dpkg::Options::="--force-confold"
        #apt-get -y dist-upgrade
		apt-get auto-remove -y

		apt-get install -y htop docker-compose
	SHELL

	# Tell Vagrant to install Docker CE
	config.vm.provision "docker"
end
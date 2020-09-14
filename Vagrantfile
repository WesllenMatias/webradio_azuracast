# -*- mode: ruby -*-
# vi: set ft=ruby :

Vagrant.configure("2") do |config|
  config.vm.box = "ubuntu/bionic64"
  config.vm.network "public_network", bridge:"wlp3s0" # "enp2s0"
  config.vm.hostname = "SRV-RADIO"
  config.vm.disk :disk, size: "30GB"
  config.vm.provider "virtualbox" do |vb|
     vb.gui = true
     vb.name = "SRV-RADIO"
     vb.memory = "2048"
     vb.cpus = 2 
   end
  config.vm.provision "shell", inline: <<-SHELL
     apt-get update -y
     apt-get upgrade -y
     apt-get install htop -y
     apt-get install lm-sensors -y
     apt-get install -f -y
     apt-ger install curl -y
     wget https://ufpr.dl.sourceforge.net/project/webadmin/webmin/1.941/webmin_1.941_all.deb
     dpkg -i webmin_1.941_all.deb
     apt-get install -f -y
     dpkg -i webmin_1.941_all.deb
     curl -fsSL https://raw.githubusercontent.com/AzuraCast/AzuraCast/master/docker.sh > docker.sh
     chmod a+x docker.sh
     ./docker.sh install
  SHELL
end

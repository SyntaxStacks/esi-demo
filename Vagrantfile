# -*- mode: ruby -*-
# vi: set ft=ruby :

# All Vagrant configuration is done below. The "2" in Vagrant.configure
# configures the configuration version (we support older styles for
# backwards compatibility). Please don't change it unless you know what
# you're doing.
Vagrant.configure(2) do |config|

  config.vm.box = "centos"

  config.vm.define "web" do |web|
    web.vm.provision "shell", path: "provision-web.sh"
    web.vm.provision "file", source: "index.php", destination: "/var/www/html/index.php"
    web.vm.provision "file", source: "bootstrap.min.css", destination: "/var/www/html/bootstrap.min.css"
    web.vm.provision "file", source: "catfacts.php", destination: "/var/www/html/catfacts.php"
    web.vm.network "private_network", ip: "192.168.50.4"
    web.vm.network :forwarded_port, host: 8080, guest: 80
  end

  config.vm.define "edge" do |edge|
    edge.vm.provision "file", source: "default.vcl", destination: "/vagrant/default.vcl"
    edge.vm.provision "shell", path: "provision-edge.sh"
    edge.vm.network :forwarded_port, host: 8081, guest: 6081
  end
end

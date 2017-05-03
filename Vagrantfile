# -*- mode: ruby -*-
# vi: set ft=ruby :

Vagrant.configure(2) do |config|
    config.vm.box = "precise64"
    config.vm.box_url = "http://files.vagrantup.com/precise64.box"
    config.vm.hostname = "bullet-base"
    config.vm.network "private_network", ip: "192.168.33.30"

    config.vm.synced_folder "./bullet-base", "/home/vagrant/bullet-base"

    config.vm.provision :shell, path: "./vagrant-setup/install-rvm.sh", args: "stable", privileged: false
    config.vm.provision :shell, path: "./vagrant-setup/install-ruby.sh", args: "2.2.3 rails haml", privileged: false
    config.vm.provision :shell, path: "./vagrant-setup/install-ruby.sh", args: "1.9.3", privileged: false
    config.vm.provision :shell, path: "./vagrant-setup/install-git.sh", privileged: false

    config.push.define "heroku" do |push|
      push.app = "Bullet-base"
      push.dir = "bullet-base"
      push.remote = "heroku"
    end
end

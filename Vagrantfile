# -*- mode: ruby -*-
# vi: set ft=ruby :
Vagrant.configure('2') do |config|
  config.vm.box      = 'ubuntu/trusty64'
  config.vm.hostname = 'rails-dev-box'

  config.vm.network :forwarded_port, guest: 3000, host: 3000
  config.vm.network :forwarded_port, id: "ssh", guest: 22, host: 2227

  config.vm.network "private_network", ip: "192.168.33.40"
  config.vm.synced_folder '../tachibana-system', '/var/www', nfs: { mount_options: ["dmode=777,fmode=777"] }

  config.vm.provision :shell, path: 'bootstrap.sh', keep_color: true

  config.vm.provider :virtualbox do |vb|
    vb.customize ["modifyvm", :id, "--memory", 1024]
  end
end

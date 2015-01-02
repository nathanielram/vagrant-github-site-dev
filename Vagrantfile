# -*- mode: ruby -*-
# vi: set ft=ruby :

Vagrant.configure(2) do |config|

  config.vm.box = "ubuntu/trusty64"

  config.vm.network "forwarded_port", guest: 80, host: 8080
  config.vm.network :forwarded_port, guest: 3000, host: 3000

  config.vm.provider "virtualbox" do |vb|
  #   # Display the VirtualBox GUI when booting the machine
  #   vb.gui = true
  #
  #   # Customize the name of the VM
      vb.name = "vagrant-github-site-dev"
  end

  # Enable Berkshelf
  config.berkshelf.enabled = true

  # Ensures Chef is running latest version
  config.omnibus.chef_version = :latest

  config.vm.provision :chef_solo do |chef|
    chef.cookbooks_path = ["cookbooks", "site-cookbooks"]
    chef.roles_path = "roles"

    root_dir = File.dirname(File.expand_path(__FILE__))
    nodes = Dir[File.join(root_dir,'nodes','*.json')]
    nodes.each do |file|
      node_json = JSON.parse(File.read(file))
      chef.json = node_json
    end
  end
end

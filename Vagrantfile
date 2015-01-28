# -*- mode: ruby -*-
# vi: set ft=ruby :

Vagrant.configure(2) do |config|

  config.vm.box = "ubuntu/trusty64"

  config.vm.network :forwarded_port, guest: 4000, host: 4000

  config.berkshelf.enabled = true

  config.omnibus.chef_version = :latest

  config.vm.provision "shell", path: "fix-libssl.sh"

  config.vm.provision :chef_solo do |chef|
    chef.roles_path = "roles"
    chef.add_role "server"

    chef.json = 
      {
        :rbenv => {
          :rubies => ["2.1.5"],
          :global => "2.1.5",
          :gems => {
            "2.1.5" => [
              {"name" => "bundler"}
            ]
          }
        }
      }
  end
end

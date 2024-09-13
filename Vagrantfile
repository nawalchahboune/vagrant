# -*- mode: ruby -*-
# vi: set ft=ruby :

# Reading .env file and storing the values in a hash
env = {}
File.read(".env").split("\n").each do |line|
  key, value = line.split("=")
  env[key] = value
end


Vagrant.configure("2") do |config|
  config.vm.box = "generic/rhel7"
  config.vm.provider "virtualbox" do |vb|
    vb.name = "RHEL-7"
    vb.memory = "2048"
  end

  # Provisioning script to register Red Hat subscription
  config.vm.provision "shell", inline: <<-SHELL
      echo 'Enregistrement de la machine avec la souscription développeur Red Hat...'
      subscription-manager register --username '#{env['REDHAT_USERNAME']}' --password '#{env['REDHAT_PASSWORD']}' --auto-attach
  SHELL

end

## vagrant plugin install vagrant-docker-compose

Vagrant.configure("2") do |node|
  node.vm.box = "ubuntu/trusty64"
  
  node.trigger.before [:provision] do |local|
    local.info = "Getting remote packages from github..."
    local.run = { inline: "git clone https://github.com/flyve-mdm/docker-environment.git src/" }
  end

  config.vm.provision :docker
  config.vm.provision :docker_compose, yml: "/vagrant/src/docker-compose.yml", rebuild: true, run: "always"
end

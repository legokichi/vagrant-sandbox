Vagrant.configure("2") do |config|
  # https://docs.vagrantup.com
  config.vm.box = "ubuntu/bionic64"
  # config.vm.network "forwarded_port", guest: 80, host: 8080
  # config.vm.network "public_network"
  config.vm.synced_folder "./data", "/vagrant_data"

  # config.vm.provider "virtualbox" do |vb|
  #   vb.gui = true
  #   vb.memory = "1024"
  # end

  config.vm.provision "docker"
  config.vm.provision "shell", inline: <<-SHELL
    apt-get update
    curl -L "https://github.com/docker/compose/releases/download/1.22.0/docker-compose-$(uname -s)-$(uname -m)" -o /usr/local/bin/docker-compose
    chmod +x /usr/local/bin/docker-compose
  SHELL
end

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
    export DEBIAN_FRONTEND "noninteractive"
    apt-get update -y
    apt-get -y \
      -o Dpkg::Options::="--force-confdef" \
      -o Dpkg::Options::="--force-confold" dist-upgrade
    
    # apt-get install -y \
    #   apt-transport-https software-properties-common ppa-purge apt-utils \
    #   ca-certificates git curl wget \
    #   tar zip unzip zlib1g-dev bzip2 libbz2-dev \
    #   openssl libssl-dev \
    #   zsh vim screen tree htop \
    #   net-tools lynx iftop traceroute \
    #   sudo
    curl -L "https://github.com/docker/compose/releases/download/1.22.0/docker-compose-$(uname -s)-$(uname -m)" -o /usr/local/bin/docker-compose
    chmod +x /usr/local/bin/docker-compose
z
    apt-get install -y -f
    apt-get update -y
    apt-get upgrade -y
    apt-get dist-upgrade -y
    apt-get clean -y
    apt-get autoremove -y
    apt-get autoclean -y
    rm -rf /var/lib/apt/lists/* /var/cache/apt/archives/*    
  SHELL
end

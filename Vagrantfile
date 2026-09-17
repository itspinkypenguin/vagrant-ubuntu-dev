Vagrant.configure("2") do |config|

  config.vm.box = "bento/ubuntu-24.04"

  config.vm.define "ubuntu-dev" do |vm|
    vm.vm.hostname = "ubuntu-dev"
  end

  config.vm.provider "virtualbox" do |vb|
    vb.name = "ubuntu-dev"
    vb.memory = 4096
    vb.cpus = 4
  end

  config.vm.provision "shell", inline: <<-SHELL

    apt-get update

    apt-get install -y \
      ca-certificates \
      curl \
      wget \
      git \
      vim \
      nano \
      htop \
      tree \
      zip \
      unzip \
      jq \
      net-tools \
      iproute2 \
      dnsutils \
      gnupg \
      lsb-release \
      software-properties-common \
      build-essential \
      python3 \
      python3-pip \
      python3-venv \
      nginx

    systemctl enable --now nginx

    echo "ubuntu-dev provisioning finished"

  SHELL

end

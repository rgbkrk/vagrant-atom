VAGRANTFILE_API_VERSION = "2"

$script = <<SCRIPT
# The basics
sudo apt-get install -y git build-essential 
# The prerequisites
sudo apt-get install -y libgnome-keyring-dev
# Technically there are other prerequisties (node, nvm)
#   but these are satisfied by the base box from vagrantcloud
SCRIPT

Vagrant.configure(VAGRANTFILE_API_VERSION) do |config|

  config.vm.box = "urban/trusty64-node"

  config.vm.provider "virtualbox" do |vb|
      vb.customize ["modifyvm", :id, "--memory", "4096"]
      vb.customize ["modifyvm", :id, "--cpus", "2"]
      vb.gui = true
  end

  config.vm.provision "shell",
    privileged: false,
    inline: $script

  config.vm.synced_folder "atom", "/atom", create: true

end

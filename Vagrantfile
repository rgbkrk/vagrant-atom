VAGRANTFILE_API_VERSION = "2"

$script = <<SCRIPT
# The basics
sudo apt-get install -y git build-essential 

# The prerequisites
# Technically there are other prerequisties (node, nvm)
#   but these are satisfied by the base box from vagrantcloud
sudo apt-get install -y libgnome-keyring-dev

# Hack/workaround for Atom's build scripts expecting a particular libudev
sudo ln -sf /lib/x86_64-linux-gnu/libudev.so.1 /lib/x86_64-linux-gnu/libudev.so.0

# Now to actually build
cd /atom
script/build
sudo script/grunt install

# To actually use atom within this VM, you need ubuntu desktop
sudo apt-get install ubuntu-desktop
SCRIPT

Vagrant.configure(VAGRANTFILE_API_VERSION) do |config|

  config.vm.box = "urban/trusty64-node"

  config.vm.provider "virtualbox" do |vb|
      vb.customize ["modifyvm", :id, "--memory", "4096"]
      vb.customize ["modifyvm", :id, "--cpus", "2"]

      # Vagrant runs headless by default
      # I'm assuming you want to actually *use* atom
      vb.gui = true
  end

  config.vm.provision "shell",
    privileged: false,
    inline: $script

  # Change this to where you have atom cloned from
  # This version uses the linked submodule
  config.vm.synced_folder "atom", "/atom", create: true

end

# -*- mode: ruby -*-
# vi: set ft=ruby :

# All Vagrant configuration is done below. The "2" in Vagrant.configure
# configures the configuration version (we support older styles for
# backwards compatibility). Please don't change it unless you know what
# you're doing.
Vagrant.configure("2") do |config|
  # The most common configuration options are documented and commented below.
  # For a complete reference, please see the online documentation at
  # https://docs.vagrantup.com.

  # Every Vagrant development environment requires a box. You can search for
  # boxes at https://vagrantcloud.com/search.
  config.vm.box = "ubuntu/bionic64"

  # Disable automatic box update checking. If you disable this, then
  # boxes will only be checked for updates when the user runs
  # `vagrant box outdated`. This is not recommended.
  # config.vm.box_check_update = false

  # Create a forwarded port mapping which allows access to a specific port
  # within the machine from a port on the host machine. In the example below,
  # accessing "localhost:8080" will access port 80 on the guest machine.
  # NOTE: This will enable public access to the opened port
  # config.vm.network "forwarded_port", guest: 80, host: 8080

  # Create a forwarded port mapping which allows access to a specific port
  # within the machine from a port on the host machine and only allow access
  # via 127.0.0.1 to disable public access
  # config.vm.network "forwarded_port", guest: 80, host: 8080, host_ip: "127.0.0.1"

  # Create a private network, which allows host-only access to the machine
  # using a specific IP.
  # config.vm.network "private_network", ip: "192.168.33.10"

  # Create a public network, which generally matched to bridged network.
  # Bridged networks make the machine appear as another physical device on
  # your network.
  # config.vm.network "public_network"

  # Share an additional folder to the guest VM. The first argument is
  # the path on the host to the actual folder. The second argument is
  # the path on the guest to mount the folder. And the optional third
  # argument is a set of non-required options.
  config.vm.synced_folder ".", "/data"

  # Provider-specific configuration so you can fine-tune various
  # backing providers for Vagrant. These expose provider-specific options.
  # Example for VirtualBox:
  config.vm.network "forwarded_port", guest: 8888, host: 8888
  config.vm.provision "file", source: "build.sh", destination: "build.sh"
  config.vm.provision "file", source: "chipwhisperer5-docker/run.sh", destination: "cwrun.sh"
  config.vm.provision "shell",
   inline: "/bin/bash build.sh" 
  config.vm.provider "virtualbox" do |vb|
  #   # Display the VirtualBox GUI when booting the machine
     vb.gui = false
  #
  #   # Customize the amount of memory on the VM:
    vb.memory = "2048"
    vb.customize ["modifyvm", :id, "--usb", "on"]
    vb.customize ["modifyvm", :id, "--usbxhci", "on"]
    vb.gui = true
    vb.name = "Hardware Hacking"
    vb.customize ["modifyvm", :id, "--uartmode1", "disconnected"]
    vb.customize ['usbfilter', 'add', '0', '--target', :id, '--name', 'NewAE Technology Inc. ChipWhisperer Lite [0100]', '--vendorid', '0x2b3e', '--productid', '0xace2']
    vb.customize ['usbfilter', 'add', '1', '--target', :id, '--name', 'NewAE Technology Inc. ChipWhisperer Nano [0100]', '--vendorid', '0x2b3e', '--productid', '0xace0']
    vb.customize ['usbfilter', 'add', '2', '--target', :id, '--name', 'NewAE Technology Inc. ChipWhisperer Pro [0100]', '--vendorid', '0x2b3e', '--productid', '0xace3']
    vb.customize ['usbfilter', 'add', '2', '--target', :id, '--name', 'NewAE Technology Inc. ChipWhisperer CW305', '--vendorid', '0x2b3e', '--productid', '0xc305']
    vb.customize ['usbfilter', 'add', '2', '--target', :id, '--name', 'NewAE Technology Inc. Ballistic Gel', '--vendorid', '0x2b3e', '--productid', '0xc521']
    vb.customize ['usbfilter', 'add', '2', '--target', :id, '--name', 'Great Scott Gadgets GreatFET', '--vendorid', '0x1d50', '--productid', '0x60e6']
    vb.memory = "2048"

  end
  #
  # View the documentation for the provider you are using for more
  # information on available options.

  # Enable provisioning with a shell script. Additional provisioners such as
  # Ansible, Chef, Docker, Puppet and Salt are also available. Please see the
  # documentation for more information about their specific syntax and use.
  # config.vm.provision "shell", inline: <<-SHELL
  #   apt-get update
  #   apt-get install -y apache2
  # SHELL
end


Vagrant.configure("2") do |config|

  config.vm.box = "ubuntu/focal64"

  config.vm.box_check_update = false
  config.vm.define "db"
  

  # Create a private network, which allows host-only access to the machine
  # using a specific IP.
  config.vm.network "public_network", ip: "192.168.10.20", bridge: "enp6s0"

  # Example for VirtualBox:
  #
  config.vm.provider "virtualbox" do |vb|
  # Display the VirtualBox GUI when booting the machine
    vb.gui = false
    vb.name = "mariadb"
  
  # Customize the amount of memory on the VM:
    vb.memory = 512
    vb.cpus = 2
  end


  config.vm.provision "ansible" do |ansible|    
    ansible.playbook = "ansible/db_install.yaml"  
  end

  # Enable provisioning with a shell script.
  # config.vm.provision "shell", inline: <<-SHELL
  #   apt-get update
  #   apt-get install -y apache2
  # SHELL
end

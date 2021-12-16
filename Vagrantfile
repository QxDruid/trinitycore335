
Vagrant.configure("2") do |config|

  config.vm.box_check_update = false

  # Creates Database VM
  config.vm.define "db" do |db|
    db.vm.box = "ubuntu/focal64"
    # Create a private network, which allows host-only access to the machine using a specific IP.
    db.vm.network "public_network", ip: "192.168.10.20", bridge: "enp6s0"

    # Customize the amount of memory and cpu on the VM:
    db.vm.provider "virtualbox" do |vb|
      vb.gui = false
      vb.name = "mariadb"
      vb.memory = 512
      vb.cpus = 1  
    end

  # Provision section 
    db.vm.provision "ansible" do |ansible|    
      ansible.playbook = "ansible/db_install.yaml"  
    end
  end

# -----------------------------------------------------------------------------------------------------
  # Creates Trinitycore Worldserver VM
  config.vm.define "worldserver" do |ws|
    ws.vm.box = "ubuntu/focal64"
    
    # Create a private network, which allows host-only access to the machine using a specific IP.
    ws.vm.network "public_network", ip: "192.168.10.21", bridge: "enp6s0"

    # Customize the amount of memory and cpu on the VM:
    ws.vm.provider "virtualbox" do |vb|
      vb.gui = false
      vb.name = "worldserver"
      vb.memory = 1024
      vb.cpus = 1
    end

  # Provision section 
    ws.vm.provision "ansible" do |ansible|    
      ansible.playbook = "ansible/worldserver_up.yaml"  
    end
  end

# -----------------------------------------------------------------------------------------------------
   # Creates Trinitycore Authserver VM
  config.vm.define "authserver" do |as|
    as.vm.box = "ubuntu/focal64"
    
    # Create a private network, which allows host-only access to the machine using a specific IP.
    as.vm.network "public_network", ip: "192.168.10.22", bridge: "enp6s0"

    # Customize the amount of memory and cpu on the VM:
    as.vm.provider "virtualbox" do |vb|
      vb.gui = false
      vb.name = "authserver"
      vb.memory = 1024
      vb.cpus = 1
    end

  # Provision section 
    as.vm.provision "ansible" do |ansible|    
      ansible.playbook = "ansible/authserver_up.yaml"  
    end
  end

# -----------------------------------------------------------------------------------------------------

  # Creates Trinitycore build VM
  config.vm.define "build" do |build|
    build.vm.box = "ubuntu/focal64"
    
    # Create a private network, which allows host-only access to the machine using a specific IP.
    build.vm.network "public_network", ip: "192.168.10.21", bridge: "enp6s0"

    # Customize the amount of memory and cpu on the VM:
    build.vm.provider "virtualbox" do |vb|
      vb.gui = false
      vb.name = "build_VM"
      vb.memory = 4096
      vb.cpus = 2
    end

  # Provision section 
    build.vm.provision "ansible" do |ansible|    
      ansible.playbook = "ansible/build.yaml"  
    end
  end

end
  
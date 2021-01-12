Vagrant.configure("2") do |config|
    config.vm.box  = "ubuntu/bionic64"

    config.vm.define "ansibleMaster" do |ansibleMaster|
        ansibleMaster.vm.provider "virtualbox" do |v|
            v.name = "ansibleMaster"
            v.memory = 512
            v.cpus = 1
        end
        ansibleMaster.vm.network "public_network", bridge: "Intel(R) Dual Band Wireless-AC 8265", ip: "192.168.0.10"
        ansibleMaster.vm.provision "shell", 
            inline: "apt-get update && apt-get install ansible && \
                     cat /vagrant/configs/id_bionic.pub >> .ssh/authorized_keys"
        
    end

    config.vm.define "wordpress" do |m|
        m.vm.provider "virtualbox" do |v|
            v.name = "wordpress"
        end
        m.vm.network "public_network", bridge: "Intel(R) Dual Band Wireless-AC 8265", ip: "192.168.0.11"
        m.vm.provision "shell", 
            inline: "apt-get update && \
                     cat /vagrant/configs/id_bionic.pub >> .ssh/authorized_keys && \
                     sudo ln -s /usr/bin/python3 /usr/bin/python"
    end

    config.vm.define "mysql" do |m|
        m.vm.provider "virtualbox" do |v|
            v.name = "mysql"
        end
        m.vm.network "public_network", bridge: "Intel(R) Dual Band Wireless-AC 8265", ip: "192.168.0.12"
        m.vm.provision "shell", 
            inline: "apt-get update && \
                     cat /vagrant/configs/id_bionic.pub >> .ssh/authorized_keys && \
                     sudo ln -s /usr/bin/python3 /usr/bin/python"
    end

end
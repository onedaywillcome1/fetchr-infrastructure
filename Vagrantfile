VAGRANTFILE_API_VERSION = "2"

Vagrant.configure(VAGRANTFILE_API_VERSION) do |config|
  config.vm.define "jenkinsci" do |jenkinsci|
    jenkinsci.vm.box = "geerlingguy/ubuntu1604"
    jenkinsci.ssh.insert_key = false
    jenkinsci.vm.synced_folder ".", "/vagrant", disabled: true

    jenkinsci.vm.hostname = "jenkinsci"
    jenkinsci.vm.network :private_network, ip: "192.168.33.70"

    jenkinsci.vm.provider :virtualbox do |v|
      v.name = "jenkinsci"
      v.memory = 512
      v.cpus = 2
      v.customize ["modifyvm", :id, "--natdnshostresolver1", "on"]
      v.customize ["modifyvm", :id, "--ioapic", "on"]
    end

    jenkinsci.vm.provision "ansible" do |ansible|
      ansible.playbook = "ansible/playbook.yml"
      ansible.inventory_path = "ansible/inventory"
      ansible.sudo = true
    end
  end

  config.vm.define "dev" do |dev|
    dev.vm.box = "geerlingguy/ubuntu1604"
    dev.ssh.insert_key = false
    dev.vm.synced_folder ".", "/vagrant", disabled: true

    dev.vm.hostname = "dev"
    dev.vm.network :private_network, ip: "192.168.33.71"

    dev.vm.provider :virtualbox do |v|
      v.name = "dev"
      v.memory = 512
      v.cpus = 2
      v.customize ["modifyvm", :id, "--natdnshostresolver1", "on"]
      v.customize ["modifyvm", :id, "--ioapic", "on"]
    end

    dev.vm.provision "ansible" do |ansible|
      ansible.playbook = "ansible/playbook.yml"
      ansible.inventory_path = "ansible/inventory"
      ansible.sudo = true
    end
  end


end

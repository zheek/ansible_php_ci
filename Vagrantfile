VAGRANTFILE_API_VERSION = "2"

Vagrant.configure(VAGRANTFILE_API_VERSION) do |config|

   config.vm.provider "virtualbox" do |v|
      v.customize ["modifyvm", :id, "--memory", "1536"]
      v.customize ["modifyvm", :id, "--graphicscontroller", "vboxvga"]
      v.customize ["modifyvm", :id, "--accelerate3d", "on"]
      v.customize ["modifyvm", :id, "--ioapic", "on"]
      v.customize ["modifyvm", :id, "--vram", "128"]
      v.customize ["modifyvm", :id, "--hwvirtex", "on"]
   end

  config.vm.define 'htpc' do |machine|
    machine.vm.box = "ubuntu/trusty64"
    machine.vm.hostname = 'htpc-vagrant'
    machine.vm.network :private_network, ip: "192.168.2.101"
  end

  config.vm.synced_folder "./", "/home/vagrant/repos" 

  config.vm.provision "ansible" do |ansible|
    ansible.playbook = "ansible/provision.yml"
    ansible.sudo = true
    ansible.groups = {
      "htpc-machine" => ["htpc"],
      "all_groups:children" => ["htpc-machine"]
    }
  #   ansible.verbose = 'vvvv'
  end
end


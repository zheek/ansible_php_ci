VAGRANTFILE_API_VERSION = "2"

Vagrant.configure(VAGRANTFILE_API_VERSION) do |config|

   config.vm.provider "virtualbox" do |v|
      v.customize ["modifyvm", :id, "--memory", "1536"]
   end

  config.vm.define 'phpci' do |machine|
    machine.vm.box = "ubuntu/trusty64"
    machine.vm.hostname = 'phpci-vagrant'
    machine.vm.network :private_network, ip: "192.168.2.103"
  end

  config.vm.provision "ansible" do |ansible|
    ansible.playbook = "ansible/provision.yml"
    ansible.sudo = true
    ansible.groups = {
      "phpci-machine" => ["phpci"],
      "all_groups:children" => ["phpci-machine"]
    }
    # ansible.verbose = 'vvvv'
  end
end


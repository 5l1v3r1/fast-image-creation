N = 0 #Number of compute nodes
Head_memory = 2048
Head_cpus = 1
Compute_memory = 2048
Compute_cpus = 1
Vagrant.configure("2") do |config|
  config.vm.define "head1", primary: true do |head|
    head.vm.hostname = "head1"
    head.vm.box = "centos/7"
    head.vm.network "private_network", ip: "192.168.1.2",
      virtualbox__intnet: "vboxnet0"
    head.vm.provider "virtualbox" do |v|
      v.name = "head1"
      v.linked_clone = true
      v.memory = 2048
      v.cpus = 1
    end
  end
  config.vm.provision :ansible do |ansible|
    ansible.limit = "all"
    ansible.playbook = "site.yml"
  end
end
Vagrant.configure("2") do |config|
  config.vm.provider "virtualbox" do |v|
    v.memory = "1024"
    v.cpus = 2
    v.customize ["modifyvm", :id, "--cpuexecutioncap", "70"]
  end
  config.vm.define "nifirh7" do |nifirh7|
#   nifirh7.vm.box = "RHEL7.5.1_baserepo"
    nifirh7.vm.box = "RH7.5_baserepo"
#   nifirh7.vm.box = "generic/rhel7"
    #nifirh7.vm.box = "iamseth/rhel-7.3"
    #nifirh7.vm.box = "javier-lopez/rhel-7.4"
    #nifirh7.vm.box = "xianlin/rhel-7.4"
    nifirh7.vm.hostname = "nifirh7"
    nifirh7.vm.network "private_network", ip: "192.168.60.198"
    nifirh7.vm.provision "shell", :inline => "sudo echo '192.168.60.198 nifirh7.local nifirh7' >> /etc/hosts"

    nifirh7.vm.provision "ansible" do |ansible|
      ansible.playbook = "deploy_nifi.yml"
      ansible.inventory_path = "vagrant_hosts"
      #ansible.tags = ansible_tags
      #ansible.verbose = ansible_verbosity
      #ansible.extra_vars = ansible_extra_vars
      #ansible.limit = ansible_limit
    end
  end
end

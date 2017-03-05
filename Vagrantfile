# -*- mode: ruby -*-
# vi: set ft=ruby :
boxes = [
  {
  :name => "centos-7",
  :box => "centos/7",
  :cpu => "33",
  :ram => "512"
  },
  {
  :name => "debian-jessie",
  :box => "debian/jessie64",
  :cpu => "33",
  :ram => "512"
  },
  {
  :name => "ubuntu-xenial",
  :box => "ubuntu/xenial64",
  :cpu => "33",
  :ram => "512"
  },
]

Vagrant.configure(2) do |config|
  
  if Vagrant.has_plugin?("vagrant-vbguest")
    config.vbguest.auto_update = false
  end
  
  config.vm.provider "virtualbox" do |vb|
    vb.memory = "512"
    vb.customize ["modifyvm", :id, "--usbehci", "off"]
  end
  
  boxes.each do |box|
    config.vm.define box[:name] do |vms|
      vms.vm.box = box[:box]
      vms.vm.hostname = "#{box[:name]}"

      vms.vm.provider "virtualbox" do |v|
        v.customize ["modifyvm", :id, "--cpuexecutioncap", box[:cpu]]
        v.customize ["modifyvm", :id, "--memory", box[:ram]]
      end

      if box[:name].eql? "ubuntu1604"
        vms.vm.provision "shell",
        inline: "echo 'Installing python 2 required by Ansible.' && sudo apt-get -y install python-minimal"
      end

      vms.vm.provision :ansible do |ansible|
        ansible.playbook = "tests/vagrant.yml"
        ansible.verbose = "v"
      end
    end
  end
end

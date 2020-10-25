# -*- mode: ruby -*-
# vi: set ft=ruby :

Vagrant.configure("2") do |config|
  config.vm.box = "centos/8"
  #config.vm.box = "galaxy3/vulpter"
  #config.vm.box_version = "20200930.09.51"
  config.vm.hostname = "vulpter"
  #config.vbguest.auto_update = false

  config.vm.network "private_network", ip: "10.55.55.8"

  #config.vm.synced_folder	"../../",	"/vagrant", owner: "2001", group: "2001"
  #config.vm.synced_folder "~/repos/uci", "/repos", owner: "2001", group: "2001", create: true
  #config.vm.synced_folder "../../Downloads", "/Downloads", owner: "2001", group: "2001", create: true
  #config.vm.synced_folder "../../log/nakadia", "/var/log/", owner: "2001", group: "2001", create: true

# config.vm.network "forwarded_port", guest: 8000, host: 8000, host_ip: "127.0.0.1", auto_correct: true
  config.vm.network "forwarded_port", guest: 3389, host: 3389, host_ip: "127.0.0.1", auto_correct: true
  config.vm.network "forwarded_port", guest: 5901, host: 5901, host_ip: "127.0.0.1", auto_correct: true

  config.vm.provider "virtualbox" do |vb|
    # Display the VirtualBox GUI when booting the machine
    # Uncomment ONE the lines below to control how much RAM Vagrant gives the VM
    # We recommend starting with 4096 (4Gb), and moving down if necessary
    # vb.memory = "1024" # 1Gb
    # vb.memory = "2048" # 2Gb
    # vb.memory = "4096" # 4Gb
    vb.name = "Vulpter (CentOS)"
    vb.gui = true
    vb.cpus = "4"
    vb.memory = "4096"
    vb.customize ["modifyvm", :id, "--cpuexecutioncap", "50"]

    vb.customize ['modifyvm', :id, '--vrde', 'on']
    vb.customize ['modifyvm', :id, '--vrdeport', '5008']
    vb.customize ['modifyvm', :id, '--graphicscontroller', 'vboxsvga']
    #vb.customize ['modifyvm', :id, '--firmware', 'efi64']
    #vb.customize ['modifyvm', :id, '--nictype1', 'virtio']
  end
   config.vm.provision "shell", inline: <<-SHELL
   hostname
   sudo dnf install python3 -y
   su - vagrant -c "python3 -m pip install --user ansible"
SHELL
  config.vm.provision "ansible" do |ansible|
    ansible.playbook = "playbook.yml"
  end
end
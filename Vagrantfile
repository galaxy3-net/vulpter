# -*- mode: ruby -*-
# vi: set ft=ruby :

Vagrant.configure("2") do |config|
  config.vm.box = "centos/8"
  config.vm.hostname = "centosbox"

  #config.vm.network "private_network", ip: "10.55.55.8"

  config.vm.synced_folder	"../../",	"/vagrant", owner: "2001", group: "2001"
  config.vm.synced_folder "~/repos/uci", "/repos", owner: "2001", group: "2001", create: true
  config.vm.synced_folder "../../Downloads", "/Downloads", owner: "2001", group: "2001", create: true
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
    vb.name = "vulpter"
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
#  config.vm.provision "shell", inline: <<-SHELL
#    tr -d '\r' < /vagrant/functions/ready >/usr/local/bin/ready && chmod 0700 /usr/local/bin/ready
#    /usr/local/bin/ready
#    /usr/local/bin/install_pkgs
#    /usr/local/bin/pull_repos
#    iptables -A INPUT -m state --state ESTABLISHED,RELATED -j ACCEPT
#    iptables -A INPUT -p tcp --dport 3389 -m state --state NEW -j ACCEPT

#    setup_xrdp
#    setup_vnc
#HELL
#nd

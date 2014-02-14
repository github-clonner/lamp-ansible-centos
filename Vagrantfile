# -*- mode: ruby -*-
# vi: set ft=ruby :

Vagrant.configure("2") do |config|
  # All Vagrant configuration is done here. The most common configuration
  # options are documented and commented below. For a complete reference,
  # please see the online documentation at vagrantup.com.
  

  config.vm.box = "centos-64-x64-vbox4210"
  config.vm.box_url = "http://puppet-vagrant-boxes.puppetlabs.com/centos-64-x64-vbox4210.box"
  config.vm.hostname = "inabox-lamp-ansible-centos"
  

  # network config
  config.vm.network :private_network, ip: "192.168.56.101"
  config.vm.network :forwarded_port, guest: 80, host: 8080
  # config.vm.network :forwarded_port, guest: 8080, host:8081 
  

  # Run our ansible modules
  config.vm.provision "ansible" do |ansible|
    ansible.playbook = "playbook.yml"
    ansible.sudo = true
  end


  # Install scap
  config.vm.provision :shell, :path => "audit/resources/scripts/scap-install.sh"

  # Run simple scap test
  config.vm.provision :shell, :path => "audit/resources/scripts/oscap-rhel6-test2.sh"

  # Run stig-rhel6-server scap test
  config.vm.provision :shell, :path => "audit/resources/scripts/oscap-rhel6.sh"

end

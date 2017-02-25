# -*- mode: ruby -*-
# vi: set ft=ruby :


VAGRANTFILE_API_VERSION = "2"
Vagrant.require_version ">= 1.7.2"

# All Vagrant configuration is done below. The "2" in Vagrant.configure
# configures the configuration version. Please don't change it unless you know what
# you're doing.
Vagrant.configure(2) do |config|

  #config.ssh.insert_key = true
  config.vm.box = "thesteve0/openshift-origin"
  config.vm.provider "virtualbox"
  #uncomment this line if you downloaded the box and want to use it instead
  #config.vm.box = "openshift3"
  config.vm.box_check_update = true
  #config.vm.network "private_network", ip: "10.2.2.2"
  config.vm.synced_folder ".", "/vagrant", disabled: true
  config.vm.provision :shell , inline: "sudo ifup eth1"
  
  #adding this in for debugging purposes. This should work even if the 10.2.2.2 virtual nic doesn't work
  #config.vm.network "forwarded_port", guest: 8443, host: 8443




  config.vm.provider "virtualbox" do |vb|
     #   vb.gui = true
     vb.memory = "5120"
     vb.cpus = 2
     vb.name = "openshift-origin"
     #commented out because of issues with F23
     #vb.customize ["modifyvm", :id, "--ioapic", "on"]
     #vb.customize ["modifyvm", :id, "--natdnshostresolver1", "on"]
  end

  config.vm.provision "shell", inline: <<-SHELL
    echo
    echo "Successfully started and provisioned VM with 2 cores and 5 G of memory."
    echo "To modify the number of cores and/or available memory modify your local Vagrantfile"
    echo
    echo "You can now access the OpenShift console on: https://10.2.2.2:8443/console"
    echo
    echo "Configured users are (<username>/<password>):"
    echo     "admin/admin"
    echo     "user/user"
    echo "But, you can also use any username and password combination you would like to create"
    echo "a new user."
    echo
    echo "You can find links to the client libraries here: https://www.openshift.org/vm"
    echo "If you have the oc client library on your host, you can also login from your host."
    echo
    echo "To use OpenShift CLI, run:"
    echo "$ oc login https://10.2.2.2:8443"
    echo
	echo  "To start Web Console"
	echo  "vagrant  ssh" 
	echo  " ip  addr" 
	echo  "sudo ifup eth1" 
  SHELL

end

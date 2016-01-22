# -*- mode: ruby -*-
# vi: set ft=ruby :
require './parameters.rb'
include MyVars

VAGRANTFILE_API_VERSION = "2"

Vagrant.configure(VAGRANTFILE_API_VERSION) do |config|
  
  config.vm.define "debian" do |debian_config|
    debian_config.vm.box = "oar-team/debian8"
    # debian_config.vm.box_url = "http://downloads.shadoware.org/wheezy64.box"
    debian_config.vm.hostname = 'debian'
    debian_config.vm.network :"private_network", ip: "192.168.110.20"
    debian_config.vm.synced_folder PATH_SHARE_FOLDER, PATH_MOUNT_FOLDER, disabled: true, type: "nfs"

    debian_config.vm.provider :virtualbox do |v|
      v.name = 'debian-7'
    end
  end

  config.vm.define "centos" do |centos_config|
    centos_config.vm.box = "chef/centos-6.5"
    centos_config.vm.hostname = 'centos'
    centos_config.vm.network :"private_network", ip: "192.168.110.21"
    centos_config.vm.synced_folder PATH_SHARE_FOLDER, PATH_MOUNT_FOLDER, disabled: true, type: "nfs"

    centos_config.vm.provider :virtualbox do |v|
      v.name = 'centos-6'
    end
  end

  config.vm.define "ubuntu" do |ubuntu_config|
    ubuntu_config.vm.box = "chef/ubuntu-14.04"
    ubuntu_config.vm.hostname = 'ubuntu'
    ubuntu_config.vm.network :"private_network", ip: "192.168.110.22"
    ubuntu_config.vm.synced_folder PATH_SHARE_FOLDER, PATH_MOUNT_FOLDER, disabled: true, type: "nfs"

    ubuntu_config.vm.provider :virtualbox do |v|
      v.name = 'ubuntu'
    end
  end

  config.vm.provision :ansible do |ansible|
    ansible.inventory_path = "devops/hosts"
    ansible.playbook = "devops/playbook.yml"
    ansible.verbose = ANSIBLE_VERBOSE
    # ansible.limit = 'all'
  end
end

# -*- mode: ruby -*-
# vi: set ft=ruby :

# Vagrantfile API/syntax version. Don't touch unless you know what you're doing!
VAGRANTFILE_API_VERSION = '2'

Vagrant.configure(VAGRANTFILE_API_VERSION) do |config|
  # All Vagrant configuration is done here. The most common configuration
  # options are documented and commented below. For a complete reference,
  # please see the online documentation at vagrantup.com.

  # Every Vagrant virtual environment requires a box to build off of.
  config.vm.box = 'trusty-server-cloudimg-amd64-vagrant-disk1'
  config.vm.box_url = 'https://cloud-images.ubuntu.com/vagrant/trusty/current/trusty-server-cloudimg-amd64-vagrant-disk1.box'

  config.vm.provider :virtualbox do |vb|
    vb.customize ['modifyvm', :id, '--natdnshostresolver1', 'on']
    vb.customize ['modifyvm', :id, '--natdnsproxy1', 'on']
  end

  config.vm.network :forwarded_port, guest: 5000, host: 5000

  # Replace 'jenkins.yml' with the appropriate playbook (and make sure the group is set properly, too)
  config.vm.provision 'ansible' do |ansible|
    ansible.host_key_checking = false
    ansible.playbook = 'docker.yml'
    ansible.groups = {
        'vagrant' => ['default'],
        'docker-hosts' => ['default']
    }
  end

end

# -*- mode: ruby -*-
# vi: set ft=ruby :

# Vagrantfile API/syntax version. Don't touch unless you know what you're doing!
VAGRANTFILE_API_VERSION = '2'

Vagrant.configure(VAGRANTFILE_API_VERSION) do |config|
  # All Vagrant configuration is done here. The most common configuration
  # options are documented and commented below. For a complete reference,
  # please see the online documentation at vagrantup.com.

  # Every Vagrant virtual environment requires a box to build off of.
  config.vm.box = 'ubuntu-12.04-server-amd64-vbox-4.3.10'

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

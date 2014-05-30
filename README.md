ansible-roles
=============

See the `Vagrantfile` for how to boot up a Vagrant/Virtualbox VM that get provisioned either 
as a Docker host or a Jenkins server.

Or, see `jenkins_host` for a sample inventory file.

To provision a Jenkins server, one just needs to go

    ansible-playbook -i jenkins_host jenkins.yml

To provision, for example, a Docker host:

1. Create an inventory file containing the host, as part of the docker-hosts group:

````
target ansible_ssh_host=10.10.0.1 ansible_ssh_private_key_file=~/.ssh/id_rsa

[docker-hosts]
target

````
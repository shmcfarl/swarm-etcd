# Vagrant - Docker Swarm using etcd

Example Vagrantfile ([http://www.vagrantup.com](http://www.vagrantup.com)) for running an etcd node, Docker Swarm Manager and two Docker nodes with IPv6. This setup is using Virtualbox with IPv6 support (Version 5.0 and higher - this setup is deployed on 5.0.16)

# Instructions

These instructions assume you've already installed VMware Fusion, Vagrant, and the Vagrant VMware plugin. Please refer to the documentation for those products for more information on installation or configuration.

1. After you have installed Vagrant on your system, install the following plugins:
- `vagrant plugin install virtualbox`
- `vagrant plugin install vagrant-vbguest`
- `vagrant plugin install vagrant-hostmanager`

2. Use `vagrant box add ubuntu/trusty64` to install an Ubuntu for the virtualbox provider.

3. Place the Vagrantfile from this directory into a directory on your local system.

4. From within the directory where the Vagrantfile is located, run `vagrant up --provider=virtualbox` and the environment will be built with four VMs.

5. Refernce the blog post<> for how to use this environment.
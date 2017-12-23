# Mastering Ansible

## Installation

```
pip3 install pyyaml
pip3 install ansible
pip3 install ansible --upgrade
ansible --version
```
## Simulate multiple hosts on local platform using VirtualBox and docker containers

1. Install docker
2. Install VirtualBox

Create the virtual machine named dev:
```
docker-machine create dev -d virtualbox
docker-machine ls
eval "$(docker-machine env dev)"
```

Manage SSH:
```
cd docker/env
ssh-keygen -t rsa ansible
cp ansible ansible.pub ~/.ssh
chmod 400 ~/.ssh/ansible*
cp ssh_host_config ~/.ssh/config
docker-machine ip dev
```
Change via an editor if needed the IP address in ~/.ssh/config with the one returned by the 'docker-machine ip dev' command.

Launch the containers:
```
cd docker
docker-compose up -d
```

Check if the machines are accessible: in the root folder, launch the command:
```
ansible -m ping all
```

## Start/Stop the containers and virtual machine

```
docker-machine start dev
cd docker
docker-compose up -d
```

```
cd docker
docker-compose down
docker-machine stop dev
```

## Application

We will install a 3-tier application with a loadbalancer, 2 web servers and a database.

## Playbooks

Launch a particular playbook:
```
ansible-playbook playbooks/hostname.yml
```

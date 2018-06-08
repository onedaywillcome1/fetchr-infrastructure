## Fetchr Dev & CI-CD Infrastructure Big Picture
![Alt text](docs/vagrant-big-picture.png?raw=true "Vagrant")

## Prerequisites
### MacOsX
- Download & Install Virtualbox
- Download & Install Vagrant
- Download & Install Ansible

## Infrastructure installation
- **Install ansible roles**: Execute ansible-galaxy command to get the roles
```
ansible-galaxy install -r requirements.yml
```
- **Start Vagrant**
```
vagrant up
```

## Automated Infrastructure steps
- Vagrant spins up Jenkins VM and Dev VM
- Vagrant executes ansible provisioner to install required tools in VMs.
- Jenkins is ready to have an access to AppServer(Dev)
![Alt text](docs/vagrant2.png?raw=true "Vagrant2")

## Manual steps
These steps will provide an Jenkins VM to access appserverVM via ansible.
- Create public & private key in jenkins VM
After executing (vagrant ssh jenkins) into JenkinsVM, do executing following command(type Enter until it gets done):
```
sudo su jenkins
ssh-keygen
ls -ltr ~/.ssh/

total 12
-rw-r--r-- 1 jenkins jenkins  398 Jun  8 00:42 id_rsa.pub
-rw------- 1 jenkins jenkins 1679 Jun  8 00:42 id_rsa
-rw-r--r-- 1 jenkins jenkins  222 Jun  8 01:46 known_hosts

```
- Get the public key of jenkins(~/.ssh/id_rsa.pub) and put id_rsa.pub contents into appserver(dev)'s  authorized_keys file
AppServerVM:
```
ls -ltr ~/.ssh/
total 4
-rw------- 1 vagrant vagrant 808 Jun  8 00:42 authorized_keys
```

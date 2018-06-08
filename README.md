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

## Infrastructure steps
- Vagrant spins up Jenkins VM and Dev VM
- Vagrant executes ansible provisioner to install required tools in VMs.
- Jenkins is ready to have an access to AppServer(Dev)
![Alt text](docs/vagrant2.png?raw=true "Vagrant2")

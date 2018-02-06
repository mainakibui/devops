# Ansible Vagrant Ubuntu Playbook

###### To Do
- [x] Manage users
- [x] Secure SSH
- [ ] Manage firewall
- [ ] Prepare webserver
- [ ] Deploy web-app

## Connecting to your machines after securing SSH

#Linux
Generate your ssh Key by typing the command below in your virtual machines terminal.

- ```ssh-keygen -t rsa -b 4096 -C "your_email@orgname.org"```
- Copy your ssh key/s to the servers in your inventory
-- Add the new user and their key to ssh_users variables in (*group_vars/secrets*)
-- Run the play (ansible-playbook -i hosts authentication.yml)
- You can now ssh into any machine by typing ssh username@ipaddress

#Windows
You can also generate your key on Windows

- Install PuTTY and PuTTYgen
-- Click generate and follow instructions.
-- Save the generated PRIVATE (id_rsa) and PUBLIC key (*id_rsa.ppk*) files and copy the plaintext OpenSSH authorized_keys into (*id_rsa.pub*) (take note of this location since you need to copy these files over to your linux development box too) the default location is *C:\Users\yourusername\.ssh* on windows and */home/yourusername/.ssh/* on linux
-- On linux you will only need id_rsa and id_rsa.pub files
-- On linux you will need to set the following permissions:
--- `chmod -R 0600 /home/yourusername/.ssh/`
--- `chmod -R 0600 /home/yourusername/.ssh/id_rsa`
--- `chmod -R 0644 /home/yourusername/.ssh/id_rsa.pub`
-- These files on linux should be owned by (`chown -R yourusername:yourusername /home/yourusername/.ssh/`)
-- After creating and adding the ssh keys to your local machines, add the new user and their key to ssh_users variables in (*group_vars/secrets*) to deploy the keys to your servers
-- Run the play (*ansible-playbook -i hosts authentication.yml*)
- You can now ssh into any machine by typing ssh username@ipaddress

#PuTTY
Make sure you add your public key to pageant putty authentication agent and refference the key in **Connection > SSH > Auth**

#Create your ssh key

ssh-keygen -t rsa -b 4096 -C "your_email@orgname.org"


The stack can be deployed using the following command:

ansible-playbook -i hosts provision.yml

ansible-playbook -i hosts -l puppet-master provision.yml

ansible-playbook -i hosts -l localhost localhost.yml


ansible-playbook -i hosts -l local localhost.yml

vagrant up --provision (Reset the machinr to default)

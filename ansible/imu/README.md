#Create your ssh key

ssh-keygen -t rsa -b 4096 -C "your_email@fao.org"


The stack can be deployed using the following command:

ansible-playbook -i hosts provision.yml

ansible-playbook -i hosts -l puppet-master provision.yml

ansible-playbook -i hosts -l localhost localhost.yml


ansible-playbook -i hosts -l local localhost.yml

vagrant up --provision (Reset the machinr to default)

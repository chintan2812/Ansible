# Ansible-Pipeline
## Commands to install ansible
Update Repositoryhttps://github.com/chintan2812/Ansible/settings
steps:1 - 5
sudo apt-get update

Install Ansible:
sudo apt-get install -y ansible
ansible --version
sudo nano /etc/ansible/hosts
You can create group and paste ip address like below:
[ansiblegroup]
65.2.140.xx
65.3.144.xx

sudo nano /etc/ansible/ansible.cfg 
    
Uncomment below lines 
inventory = /etc/ansible/hosts
sudo-user = root

Now, create one user in all these instance(ansible server and nodes)
sudo adduser ansible
sudo passwd ansible
now navigate the ansible user 
su - ansible 

Add User to the sudo Group
Step1: Give some privileged in all nodes(ansible server and node) using below command:

  sudo visudo 
go to inside this file and add this line

ansible ALL=(ALL) NOPASSWD:ALL
#6.Update ssh_config file
For SSH connection to node from Ansible server make changes in sshd_config file

Now we have to some changes in ssh-config file in ansible server and nodes:

sudo nano /etc/ssh/sshd_config
Then you need to uncomment these two lines

PubkeyAuthentication yes
PasswordAuthentication yes
Now we need to restart sshd service:

sudo systemctl restart sshd
Lets check the status:

sudo systemctl status sshd
#7.Ansible Master and Slave Setup
 Go to ansible server run the below command

Step1: login to ansible in ansible server using below command:

su - ansible
Step2: Run the below command to connect node:

ssh ip_address ( node ip)
#8.Setup SSH keys and share it among managed nodes
To communicate with client we have to genrate SSH key on ansible server node and exchange with Slave/Client Systems.

Step1: we need to generate ssh keygen in ansible server

ssh-keygen 
Step2: you need to inside .ssh:

cd .ssh
Step3:Now run the below command using private ip of your node:

ssh-copy-id ansible@{private address } 


Install Python-pip3:(We need to install python for amazonlinux)
sudo apt install python3-pip -y
 ( this is just comment -  Package manager for python)

Install Boto Framework - AWS SDK

Ansible will access AWS resources using boto SDK.

sudo apt-get install python3-boto -y
pip list boto | grep boto
Ignore warning in Red color.)

ansible --version

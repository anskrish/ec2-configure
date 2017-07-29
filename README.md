# ec2-configure

Varibales:

This role will launch the EC2 instance in your configured/mentioned region , please change variables based on your requirement suits
ec2/vars/main.yml

key_name: new_ubuntu
instance_type: t2.micro
security_group: launch-wizard-1
image: ami-4b133c5d
region: us-east-1

Execution:

Before executing the playbook

1. this palybook we mwntioned key name like " key_name: new_ubuntu"  put "new_ubuntu" pem  file in some location in playbook execution server.
   example:
        root@ip-172-31-5-33:~/ec2-instance-launch# ls -l /home/ubuntu/new_ubuntu.pem 
        -r-------- 1 ubuntu ubuntu 1696 Jul 29 06:47 /home/ubuntu/new_ubuntu.pem      
2. define path of your pem file in ansible config file
   
    Example:
        vim /etc/ansible/ansible.cfg
        # if set, always use this private key file for authentication, same as
        # if passing --private-key to ansible or ansible-playbook
        private_key_file = /home/ubuntu/new_ubuntu.pem 


Then execute
 
ansible-playbook ec2-launch.yml  

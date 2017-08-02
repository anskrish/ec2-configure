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


While execution , if you mentioned 2 instances in instance count,  then you have to type two time "yes" for authentication.

=====Example:=====
---below i mentioned instance count 3 , so i have ti type "yes" 3 times-----

TASK [Gathering Facts] ***************************************************************************************************************************************
The authenticity of host '172.31.0.152 (172.31.0.152)' can't be established.
ECDSA key fingerprint is 44:5d:3f:40:b7:28:dc:13:46:8b:8f:0a:4a:1e:fd:29.
Are you sure you want to continue connecting (yes/no)? The authenticity of host '172.31.12.148 (172.31.12.148)' can't be established.
ECDSA key fingerprint is 78:db:22:c4:02:84:aa:02:36:3d:33:34:3b:4c:4b:1e.
Are you sure you want to continue connecting (yes/no)? The authenticity of host '172.31.11.41 (172.31.11.41)' can't be established.
ECDSA key fingerprint is 9a:27:d2:bd:7b:61:76:61:08:af:be:48:f1:fd:65:81.
Are you sure you want to continue connecting (yes/no)? yes
yes
yes



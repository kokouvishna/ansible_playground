install aws collection (https://galaxy.ansible.com/ui/repo/published/amazon/aws/):
$ ansible-galaxy collection install amazon.aws

install boto3 (enables python to talk to the api):
$ pip install boto3

Setup Vault:
Create a password for vault:
$ openssl rand -base64 2048 > vault.pass
Add your AWS credentials using the below vault command:
$ ansible-vault create group_vars/all/pass.yml --vault-password-file vault.pass
Copy/paste your cloud access and secret keys in the upper file

# Ansible Realtime project

## Task 1

Create three(3) EC2 instances on AWS using Ansible loops
- 2 Instances with Ubuntu Distribution
- 1 Instance with Amazon Linux Distribution

Hint: Use `connection: local` on Ansible Control node.

## Task 2

Set up passwordless authentication between Ansible control node and newly created 
instances.

## Task 3

Automate the shutdown of Ubuntu Instances only using Ansible Conditionals

Hint: Use `when` condition on ansible `gather_facts`


# create ec2 instance
$ ansible-playbook create_ec2_instance.yaml --vault-password-file vault.pass 

Passwordless auth:
$ ssh-copy-id -f "-o IdentityFile <PATH TO PEM FILE>" ubuntu@<INSTANCE-PUBLIC-IP>
$ ssh -o ' IdentityFile ansible_key.pem' 'ubuntu@<INSTANCE-PUBLIC-IP>'

# shutdown instances
$ ansible-playbook -i inventory.ini create_ec2_instance.yaml --vault-password-file vault.pass 

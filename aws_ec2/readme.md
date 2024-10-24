install aws collection (https://galaxy.ansible.com/ui/repo/published/amazon/aws/):
ansible-galaxy collection install amazon.aws

install boto3 (enables python to talk to the api):
pip install boto3

Setup Vault:
Create a password for vault:
$ openssl rand -base64 2048 > vault.pass
Add your AWS credentials using the below vault command:
$ ansible-vault create group_vars/all/pass.yml --vault-password-file vault.pass
Copy/paste your cloud access and secret keys in the upper file

create ec2 instance
$ ansible-playbook -i inventory.ini aws_ec2_playbook.yaml --vault-password-file vault.pass 
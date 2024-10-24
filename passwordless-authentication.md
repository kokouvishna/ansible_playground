
EC2 Instances
Using Public Key
ssh-copy-id -f "-o IdentityFile <PATH TO PEM FILE>" ubuntu@<INSTANCE-PUBLIC-IP>
ssh-copy-id: This is the command used to copy your public key to a remote machine.
-f: This flag forces the copying of keys, which can be useful if you have keys already set up and want to overwrite them.
"-o IdentityFile ": This option specifies the identity file (private key) to use for the connection. The -o flag passes this option to the underlying ssh command.
ubuntu@: This is the username (ubuntu) and the IP address of the remote server you want to access.
Using Password
Go to the file /etc/ssh/sshd_config.d/60-cloudimg-settings.conf
Update PasswordAuthentication yes
Restart SSH -> sudo systemctl restart ssh

ssh -o ' IdentityFile /media/sf_shared_folder/deploy_1.pem' 'ubuntu@3.64.58.29'

https://galaxy.ansible.com/ui/standalone/roles/bsmeding/docker/
ansible-galaxy role init <name> => ansible-galaxy role install bsmeding.docker
check ~/.ansible/roles; there should be the new installed role (bsmeding.docker)
$ ansible-playbook -i inventory.ini docker-playbook.yaml
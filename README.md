
This is a subset of Valigator's Ansible playbooks for configuring a bare metal server in prep for using it as a Solana validator.

Check `todo.txt` for things we know we need to develop.

Check `customization.txt` for places to modify the playbooks to fit into your environment.

# PREPARATION:

sudo useradd ansible --shell /bin/bash --home /home/ansible -u 2000 
sudo mkdir -p /home/ansible/.ssh/
sudo bash -c "cat >/home/ansible/.ssh/authorized_keys <<EOF
**** PUT PUBLIC KEY HERE ****
EOF"

sudo chown -R ansible:ansible /home/ansible
sudo chmod 700 /home/ansible/.ssh/authorized_keys

sudo passwd -d ansible

id ansible

echo 'ansible ALL=(ALL) NOPASSWD:ALL' | sudo tee /etc/sudoers.d/ansible > /dev/null


# RUN:
ansible-playbook -i hosts.yml fresh_validator.yml -l **HOSTNAME**# ansible-public

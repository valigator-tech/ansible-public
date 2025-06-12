
# PREPERATION:

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





# THEN TO RUN:
ansible-playbook -i hosts.yml fresh_validator.yml -l **HOSTNAME**# ansible-public

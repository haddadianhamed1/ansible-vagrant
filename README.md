# Ansbile-vagrant

vagrant up ansible
vagrant up webserver

vagrant ssh ansible
sudo apt-get install ansible -y
or
sudo apt-get install pip -y
pip install ansible


## Generate a new key air on the ansible machine
ssh-keygen
Private key is stored in: ~/.ssh/id_rsa
Public key is stored in: ~/.ssh/id_rsa.pub

copy the content of public key and save it on webserver host
vagrant ssh webserver
sudo -s
echo ‘full content of id_rsa.pub’ > /root/.ssh/authorized_keys


## Set up inventory file on ansbile machine
echo ‘[webservers’] > hosts
echo ‘192.168.0.2’ >> hosts
# we can define multiple IP addresses or hosts under one group or add more groups like databases

# ssh-agent adds our id_rsa ke so we dont have to specify it each time
ssh-agent bash
ssh-add .ssh/id_rsa

# all the commands should be ran from /vagrant or copied to another directory of choice
## To test
ansible -i hosts -u root -m ping all

192.168.0.2 | success >> {
    "changed": false,
    "ping": "pong"
}


# to run playbook
cd /vagrant
ansible-playbook -i hosts -u root nginx.yml

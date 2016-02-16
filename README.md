# ansible-raintank-collector
Ansible play book for deploying private Raintank probes
Tested using Ansible version 1.9.2
## Requirements
User account on remote hosts with sudo access and public key from local machine add to authorized_keys file on remote host.

## Instructions
To create a private probe for Raintank add the host to the hosts file and edit raintank.yml. Input the host and change the username variable to your own username.

Edit the ansible.cfg file adding your username to 'remote_user =' and adding the path to your private ssh key file.

Add the name of the probe and API Key to files/config.json. Then run the following command.

    $ ansible-playbook raintank.yml

For CentOS run:

    $ ansible-playbook raintank_centos.yml

Once the playbook is complete ssh to the host and start the probe with the following command from ~/raintank-collector/:

    $ nohup nodejs app.js -c /etc/config.json > /dev/null 2>&1 &

For the CentOS version run:

	  $ nohup node app.js -c /etc/config.json > /dev/null 2>&1 &

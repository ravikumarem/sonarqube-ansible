Original code credits: https://github.com/MakariosNassef/SonarQube_via_Ansible

I have used the same code, and modified the variables according to our requirements and ran this ansible playbook.

To run on the Ubuntu machine (I have chosen ubuntu 22.04 specifically and tried this code), please run below few commands manually before running the playbook file. 
 ```bash
$ sudo apt install python3-pip
$ sudo pip3 install passlib
 ```

You can run these commands for temporary fix, as SonarQube requires these sizes instead of default sizes. 
```bash
$ sudo sysctl -w vm.max_map_count=262144
$ sudo sysctl -w fs.file-max=65536
```

If want to persist the changes, add the below content in the file /etc/sysctl.conf
```bash
vm.max_map_count=262144
fs.file-max=65536
```

Install Ansible, https://docs.ansible.com/ansible/latest/installation_guide/installation_distros.html
```bash
$ sudo apt update
$ sudo apt install software-properties-common
$ sudo add-apt-repository --yes --update ppa:ansible/ansible
$ sudo apt install ansible
```

I have used inventory file as just the machine IP in it, to avoid passing the PEM key. You can follow the same or you can use the above commands (in inventory file) to run the playbook. 

Let's say you wanted to use only the machine IP, then follow the commands below. Copy your machine PEM key in the machine, and once it is copied and given permission for "id_rsa" and remove the key from machine once below commands run. 

```bash
$ cp /home/ubuntu/key.pem ~/.ssh/id_rsa
$ chmod 400 ~/.ssh/id_rsa
$ eval "$(ssh-agent -s)"
$ ssh-add ~/.ssh/id_rsa
```

Run the playbook using 
```bash
$ ansible-playbook -i inventory.ini sonarqube_playbook.yml
```

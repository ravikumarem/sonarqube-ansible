Original code credits: https://github.com/MakariosNassef/SonarQube_via_Ansible

I have used the same code, and modified the variables according to our requirements and ran this ansible playbook.

To run on the Ubuntu machine( I have choosen ubuntu 22.04 specifically and tried this code), please run below few commands manually before running the playbbok file.
 ```bash
$ sudo apt install python3-pip
$ sudo pip3 install passlib
 ```

You can run these commands for temporary fix
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


Run the playbook using 
```bash
$ansible-playbook -i inventory.ini sonarqube_playbook.yml
```

# change your inventory file, according to your ubunut machine

# CLEAN CODE EVERYWHERE, FOR EVERYONE ✨

## Introduction
This Ansible playbook automates the installation of SonarQube on a Debian/Ubuntu-based system. It ensures clean code quality for all! 🧹

![1_rn-sO9oWLn9lYO7jkVO6og](https://github.com/MakariosNassef/SonarQube_via_Ansible/assets/28235504/444c376f-7791-4f32-91fd-cf246254ca91)


## Prerequisites
Before diving into the world of clean code, make sure you have the following:

- ✅ Ansible installed on your control machine.
- 🚀 SSH access to the target server.
- ⚙️ The playbook is configured with the necessary variables (e.g., `sonarqube_version`, `psql_sonar_username`, `psql_sonar_password`, etc.).

## Usage
Get ready to unleash the power of clean code with these simple steps:

1. 📥 Clone this repository or download the playbook to your local machine.

2. 🛠️ Update the playbook variables:
   - Open the playbook file (e.g., `vars/main.yml`) and set the required variables according to your setup. Pay attention to variables such as `sonarqube_version`, `psql_sonar_username`, `sonar_web_port`, etc.

3. 🚀 Run the playbook using the following command:

   ```bash
   ansible-playbook -i inventory.ym sonarqube-install.yml
   ```

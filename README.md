Configure LAMP stack with Ansible
- Ansible installation
- Create Ansible Role for:
            - common configurations
            - PHP 7
            - MYSQL 5.7
            - APACHE 2.4
- Playbook creation using the role / roles above deploys a PHP application that uses a database
- Playbook is run with a user "sudo", not root

###Ubuntu Instance-Prerequisites
            
            -Install Ubuntu 16.04 on a virtual machine
            -User: alin  ; Sudo_Password: admin
            -Internal IP: 192.168.196.50
            -Setup Path for inventory and hosts: /home/alin/Ansible/ansible-lamp-stack-playbook/ (changes can be done on /etc/ansible/ansible.cf)

            -sudo usermod -a -G sudo "user"    #add user to the group sudo
            -sudo visudo
            -"user" ALL=(ALL) NOPASSWD: ALL  #remove password for sudo commands
            
            -sudo adduser <username>
            -sudo useradd username -m -s /bin/bash 
            -sudo passwd username 

            -sudo addgroup <groupname>
            -sudo usermod -aG <groupname> <username>

            -sudo visudo
            -<username> ALL=(ALL) ALL


            -apt-get update -y
            -apt-get upgrade -y
            -apt-get install openssh-server -y
            -apt-get install git -y
            -apt-get install net-tools -y
            -apt-get install \
                -apt-transport-https \
                -ca-certificates \
                -curl \
                -software-properties-common

            -apt-get install vim
            -apt-get install docker -y ; apt-get install docker.io -y ; apt-get install docker-compose -y ;

###Install Ansible

            -apt-get update
            -apt-get install software-properties-common
            -apt-add-repository ppa:ansible/ansible
            -apt-get update
            -apt-get install ansible

            -apt install python-pip
            -pip install --upgrade pip
            -pip install --upgrade setuptools
            -pip install --ignore-installed --upgrade ansible
            ###-pip install pyOpenSSL==16.2.0
            ###-apt-get install sshpass
            ###-ansible-container init (optional)

###Ansible Commands

            -ansible all -m ping --ask-pass -vvv
            -ansible all -m ping   -vvv
            -ansible-playbook -i hosts lamp-playbook.yml --ask-pass


###Configure ansible.cfg

            -inventory      = /home/alin/Ansible/ansible-lamp-stack-playbook/hosts
            -library        = /usr/share/my_modules/
            -module_utils   = /usr/share/my_module_utils/
            -remote_port    = 22
            -roles_path     = /home/alin/Ansible/ansible-lamp-stack-playbook/roles
            -host_key_checking = False
            -sudo_flags = --set-home --stdin
            -log_path = /var/log/ansible.log
            -deprecation_warnings = False

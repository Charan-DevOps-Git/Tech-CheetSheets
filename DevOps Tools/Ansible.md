
## Basic Concepts

- **Playbook**: A YAML file containing a series of tasks to be executed on a set of hosts.
- **Task**: A single action to be performed, such as installing a package.
- **Role**: A set of related tasks and configurations grouped together.
- **Inventory**: A file listing the hosts and groups of hosts managed by Ansible.
- **Module**: A reusable, standalone script that Ansible runs on your behalf.
- **Variable**: A key-value pair used to store data that can be reused in playbooks and templates.
- **Handler**: A task that only runs when triggered by another task.

## Installation

### On Ubuntu
```
sudo apt update
sudo apt install ansible
```

## Verify Installation
```
ansible --version
```

# Configuration

## Inventory File (hosts)
```
[webservers]
web1.example.com
web2.example.com

[dbservers]
db1.example.com
db2.example.com
```

## Ansible Configuration File (ansible.cfg)
```
[defaults]
inventory = ./hosts
remote_user = your_username
```

# Basic Commands

## Ping All Hosts
```
ansible all -m ping
```

## List Hosts
```
ansible all --list-hosts
```

## Run an Ad-Hoc Command
```
ansible all -m command -a "uptime"
```

## Run a Playbook
```
ansible-playbook playbook.yml
```

# Playbook Structure

## Simple Playbook Example (playbook.yml)
```
---
- name: Ensure web servers are running
  hosts: webservers
  become: yes
  tasks:
    - name: Install Nginx
      apt:
        name: nginx
        state: present

    - name: Start Nginx service
      service:
        name: nginx
        state: started
```

# Common Modules

## Package Management
```
- name: Install a package
  apt:
    name: nginx
    state: present
```

## Service Management
```
- name: Ensure a service is running
  service:
    name: nginx
    state: started
```

## File Management
```
- name: Create a file
  file:
    path: /tmp/hello.txt
    state: touch

- name: Ensure a directory exists
  file:
    path: /etc/myapp
    state: directory
```

## User Management
```
- name: Ensure a user exists
  user:
    name: johndoe
    state: present
```

## Copy Files
```
- name: Copy a file
  copy:
    src: /local/path/file.txt
    dest: /remote/path/file.txt
```

## Templates
```
- name: Deploy a configuration file from template
  template:
    src: /local/path/file.j2
    dest: /remote/path/file.conf
```

## Execute Commands
```
- name: Run a command
  command: uptime
```

## Shell Commands
```
- name: Run a shell command
  shell: |
    echo "Hello World"
    echo "Another command"
  ```
  
# Variables

## Define Variables in Playbook
```
- name: Example with variables
  hosts: all
  vars:
    http_port: 80
  tasks:
    - name: Print the HTTP port
      debug:
        msg: "The HTTP port is {{ http_port }}"
```

## Define Variables in Inventory
```
[webservers]
web1.example.com http_port=8080
web2.example.com http_port=8080
```

## Variable File (vars.yml)
```
http_port: 80
```

## Include Variable File in Playbook
```
- name: Example with variables from file
  hosts: all
  vars_files:
    - vars.yml
  tasks:
    - name: Print the HTTP port
      debug:
        msg: "The HTTP port is {{ http_port }}"
```

# Handlers

## Using Handlers
```
- name: Example with handlers
  hosts: webservers
  tasks:
    - name: Ensure Nginx is installed
      apt:
        name: nginx
        state: present
      notify:
        - Restart Nginx

  handlers:
    - name: Restart Nginx
      service:
        name: nginx
        state: restarted
```

# Roles

## Creating a Role
```
ansible-galaxy init myrole
```

## Using a Role in a Playbook
```
- name: Example with roles
  hosts: webservers
  roles:
    - myrole
```

# Loops

## Basic Loop
```
- name: Install multiple packages
  apt:
    name: "{{ item }}"
    state: present
  with_items:
    - nginx
    - git
    - htop
```

# Conditionals

## Using Conditionals
```
- name: Conditional task
  apt:
    name: nginx
    state: present
  when: ansible_facts['os_family'] == "Debian"
```

# Useful Commands

## Check Syntax of Playbook
```
ansible-playbook playbook.yml --syntax-check
```

## Test Playbook with --check Mode
```
ansible-playbook playbook.yml --check
```

## Limit Playbook Execution to Specific Hosts
```
ansible-playbook playbook.yml --limit "web1.example.com"
```

## Running a Playbook with Tags
```
ansible-playbook playbook.yml --tags "tag_name"
```

# Resources

[Ansible Documentation](https://docs.ansible.com/)

This cheat sheet provides a comprehensive overview of Ansible, covering basic concepts, installation, configuration, common modules, variables, handlers, roles, loops, conditionals, and useful commands.

# Ansible Commands

## Ad-hoc Commands

- ansible all -m ping: Ping all hosts to check connectivity.
- ansible all -a "/bin/echo hello": Run a shell command on all hosts.
- ansible all -m yum -a "name=httpd state=present": Install a package on all hosts using the yum module.
- ansible all -m service -a "name=httpd state=started": Start a service on all hosts.
- ansible all -m copy -a "src=/path/to/local/file dest=/path/to/remote/file": Copy a file to all hosts.
- ansible all -m file -a "path=/path/to/file state=absent": Delete a file on all hosts.

# Playbooks

- Run a Playbook:
```
ansible-playbook playbook.yml
```

- Run a Playbook with a specific inventory file:
```
ansible-playbook -i inventory playbook.yml
```

- Run a Playbook with tags:
```
ansible-playbook playbook.yml --tags "tag_name"
```

# Inventory Management

- Test an Inventory File:
```
ansible-inventory -i inventory --list
```

- Display Host Information:
```
ansible-inventory -i inventory --host [hostname]
```

# Role Management

- Create a New Role:
```
ansible-galaxy init [role_name]
```

- Install Roles from Galaxy:
```
ansible-galaxy install [role_name]
```

# Vault Management

- Encrypt a File:
```
ansible-vault encrypt file.yml
```

- Decrypt a File:
```
ansible-vault decrypt file.yml
```

- Edit an Encrypted File:
```
ansible-vault edit file.yml
```

- Rekey an Encrypted File:
```
ansible-vault rekey file.yml
```

# Miscellaneous

- Check the Ansible Version:
```
ansible --version
```

- List All Installed Modules:
```
ansible-doc -l
```

- Show Documentation for a Module:
```
ansible-doc [module_name]
```

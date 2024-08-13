## Ansible

### Ansible adhoc commands

To create a file on target server
```
ansible -i inventory all -m"shell" -a "touch demofile"
```
Number of process on target server
```
ansible -i inventory all -m"shell" -a "nproc"
```
Check the disk usage on target server
```
ansible -i inventory all -m"shell" -a "df"
```
### Ansible playbook

Write a playbook which install Nginx and start it in target server

start of playbook with (---) "three hyphen"
```
---
- name: Install and Start nginx
  hosts: all
  become: true

  tasks:
    - name: Install Nginx
      apt:
        name: nginx
        state: present
    - name: Start Nginx
      service:
        name: nginx
        state: started
```
Run the Ansible playbook on target server
```
ansible-playbook -i inventory first-playbook.yml
```
Check Nginx status on target server
```
--> sudo systemctl status nginx
```
# CNC-29: Day 8 | Task 4 | Create Ansible Playbook to Install and Configure Nginx

- **Jira:** https://mail4mithunu.atlassian.net/browse/CNC-29
- **Status:** In Review
- **Assignee:** Mithun.U
- **Issue type:** Task
- **Priority:** Medium
- **Resolution:** —
- **Reporter:** Mithun.U
- **Created:** 2026-10-22T09:03:11.743Z
- **Updated:** 2026-10-22T16:17:54.885Z
- **Due date:** —
- **Labels:** ansible,nginx,playbook
- **Components:** —

## Description

Objective

Write and execute an Ansible playbook that installs Nginx on Debian, RHEL, and SUSE, enables and starts the service, and deploys a custom index.html file to the correct document root for each operating system.

Step 1: Create index.html

On the Ubuntu Ansible master, create index.html.


```
<!DOCTYPE html>
<html>
<head>
    <title>Ansible Lab</title>
</head>
<body>
    <h1>Hello from Ansible!</h1>
    <p>Nginx was installed and configured using an Ansible playbook.</p>
</body>
</html>
```

Step 2: Create nginx.yml

Create nginx.yml in the same directory.


```
---
- hosts: all
  become: true
  tasks:
    - name: Install Nginx
      package:
        name: nginx
        state: present

    - name: Start Nginx
      service:
        name: nginx
        state: started
        enabled: true

    - name: Copy index.html to Debian
      copy:
        src: index.html
        dest: /var/www/html/index.html
      when: ansible_facts["os_family"] == "Debian"

    - name: Copy index.html to RHEL
      copy:
        src: index.html
        dest: /usr/share/nginx/html/index.html
      when: ansible_facts["os_family"] == "RedHat"

    - name: Copy index.html to SUSE
      copy:
        src: index.html
        dest: /srv/www/htdocs/index.html
      when: ansible_facts["os_family"] == "Suse"
```

The package module installs Nginx using the managed node's package manager. The service module starts Nginx and enables it at boot. The when conditions select the correct document root based on the operating system family.

Step 3: Execute the playbook


```
ansible-playbook -i inventory.txt nginx.yml
```

If sudo requires a password, use:


```
ansible-playbook -i inventory.txt nginx.yml -K
```

Step 4: Verify the service

Check whether Nginx is active on all three slaves:


```
ansible all -i inventory.txt -b -m command -a "systemctl is-active nginx"
```

Verify the deployed HTML on Debian:


```
ansible debian -i inventory.txt -b -m command -a "cat /var/www/html/index.html"
```

Use /usr/share/nginx/html/index.html for RHEL and /srv/www/htdocs/index.html for SUSE.

To access the web pages externally, allow inbound HTTP traffic on TCP port 80 in the EC2 security group and open each slave's public IP in a browser.

## Attachments

- [screenshot-2026-10-22_15-51-31.png](attachments/screenshot-2026-10-22_15-51-31.png)
- [screenshot-2026-10-22_15-53-07.png](attachments/screenshot-2026-10-22_15-53-07.png)
- [screenshot-2026-10-22_15-53-50.png](attachments/screenshot-2026-10-22_15-53-50.png)

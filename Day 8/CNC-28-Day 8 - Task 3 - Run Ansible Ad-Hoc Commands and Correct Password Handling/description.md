# CNC-28: Day 8 | Task 3 | Run Ansible Ad-Hoc Commands and Correct Password Handling

- **Jira:** https://mail4mithunu.atlassian.net/browse/CNC-28
- **Status:** In Review
- **Assignee:** Mithun.U
- **Issue type:** Task
- **Priority:** Medium
- **Resolution:** —
- **Reporter:** Mithun.U
- **Created:** 2026-10-22T09:01:35.733Z
- **Updated:** 2026-10-22T16:17:26.989Z
- **Due date:** —
- **Labels:** ansible,adhoc
- **Components:** —

## Description

Objective

Create an Ansible control node and three managed EC2 instances, execute ad-hoc commands, resolve SSH authentication and host-key issues, and practise user creation and privilege escalation.

Step 1: Create the EC2 instances

Launch four EC2 instances in the same AWS region and VPC:


Instance | Operating system | Purpose
Master | Ubuntu Server | Ansible control node
Slave 1 | Debian | Managed node
Slave 2 | Red Hat Enterprise Linux | Managed node
Slave 3 | SUSE Linux Enterprise Server | Managed node

Configure a security group to allow SSH on port 22 from the administrator's IP and between instances using the same security group.

Use EC2 User Data to install Python on the slaves.

Debian:


```
#!/bin/bash
apt-get update
apt-get install -y python3
```

RHEL:


```
#!/bin/bash
dnf install -y python3
```

SUSE:


```
#!/bin/bash
zypper --non-interactive refresh
zypper --non-interactive install python3
```

Install Ansible on the Ubuntu master:


```
sudo apt update
sudo apt install ansible -y
ansible --version
```

Step 2: Configure SSH authentication

Copy the appropriate private key to the master and secure its permissions.


```
chmod 600 ~/.ssh/slaves.pem
```

Ensure that the key matches the EC2 instances' configured key pair and use the correct default SSH username for each AMI.

If SSH host-key verification fails, verify the host's fingerprint before trusting it. For a lab, host keys can be retrieved with:


```
ssh-keyscan -H SLAVE_PRIVATE_IP >> ~/.ssh/known_hosts
```

Step 3: Create the Ansible inventory

Create inventory.txt on the master.


```
[debian]
DEBIAN_IP ansible_user=admin

[rhel]
RHEL_IP ansible_user=ec2-user

[suse]
SUSE_IP ansible_user=ec2-user

[all:vars]
ansible_ssh_private_key_file=/home/ubuntu/slaves.pem
```

Replace the IP placeholders and usernames with the actual instance details.

Step 4: Test Ansible connectivity


```
ansible all -i inventory.txt -m ping
```

Expected result: each slave returns SUCCESS with "ping": "pong".

The Ansible ping module verifies SSH connectivity and remote Python execution; it is not an ICMP ping.

Step 5: Execute ad-hoc commands

Inspect the current uptime:


```
ansible all -i inventory.txt -m command -a "uptime"
```

Inspect disk usage:


```
ansible all -i inventory.txt -m command -a "df -h"
```

Check the current user with privilege escalation:


```
ansible all -i inventory.txt -m command -a "whoami" -b
```

Use -b to enable privilege escalation and -K to prompt for the become password when required.


```
ansible all -i inventory.txt -m command -a "whoami" -b -K
```

Step 6: Create a user with the user module

Create a user named testuser and set its password using a SHA-512 password hash:


```
ansible all -i inventory.txt -m user -a "name=testuser password={{ 'Test@123' | password_hash('sha512') }}" -b
```

Verify that the account exists:


```
ansible all -i inventory.txt -m command -a "id testuser" -b
```

The password_hash filter generates a password hash. Ansible may display NOT_LOGGING_PASSWORD in its output to prevent password information from being logged.

## Attachments

- [screenshot-2026-10-22_15-11-41.png](attachments/screenshot-2026-10-22_15-11-41.png)
- [screenshot-2026-10-22_15-25-01.png](attachments/screenshot-2026-10-22_15-25-01.png)
- [screenshot-2026-10-22_15-36-30.png](attachments/screenshot-2026-10-22_15-36-30.png)
- [screenshot-2026-10-22_15-37-15.png](attachments/screenshot-2026-10-22_15-37-15.png)
- [screenshot-2026-10-22_15-38-20.png](attachments/screenshot-2026-10-22_15-38-20.png)
- [screenshot-2026-10-22_15-43-09.png](attachments/screenshot-2026-10-22_15-43-09.png)

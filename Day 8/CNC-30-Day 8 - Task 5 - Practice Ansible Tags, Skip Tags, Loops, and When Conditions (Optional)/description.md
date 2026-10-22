# CNC-30: Day 8 | Task 5 | Practice Ansible Tags, Skip Tags, Loops, and When Conditions (Optional)

- **Jira:** https://mail4mithunu.atlassian.net/browse/CNC-30
- **Status:** In Review
- **Assignee:** Mithun.U
- **Issue type:** Task
- **Priority:** Medium
- **Resolution:** —
- **Reporter:** Mithun.U
- **Created:** 2026-10-22T09:03:45.116Z
- **Updated:** 2026-10-22T16:18:34.652Z
- **Due date:** —
- **Labels:** ansible,playbook,optional
- **Components:** —

## Description

Objective

Practise Ansible tags, skip tags, loops, and conditional execution using when clauses to control which tasks run on managed nodes.

Step 1: Practise tags

Add a tag to a task in nginx.yml.


```
- name: Copy index.html to Debian
  copy:
    src: index.html
    dest: /var/www/html/index.html
  when: ansible_facts["os_family"] == "Debian"
  tags: deb
```

Execute only tasks tagged deb:


```
ansible-playbook -i inventory.txt nginx.yml --tags deb
```

Skip tasks tagged deb:


```
ansible-playbook -i inventory.txt nginx.yml --skip-tags deb
```

Only tasks matching the selected tags run, except for special cases such as fact gathering and tasks tagged always.

Step 2: Practise loops

Create install.yml to install multiple packages on the Debian slave.


```
---
- hosts: debian
  become: true

  tasks:
    - name: Install packages
      apt:
        name: "{{ item }}"
        state: present
        update_cache: true
      loop:
        - git
        - curl
        - wget
        - vim
        - unzip
        - nginx
```

Run the playbook:


```
ansible-playbook -i inventory.txt install.yml
```

The loop directive executes the installation task for every package in the list. The item variable represents the current package.

Step 3: Practise when conditions

Use the when condition to run a task only on Debian.


```
- name: Copy index.html to Debian
  copy:
    src: index.html
    dest: /var/www/html/index.html
  when: ansible_facts["os_family"] == "Debian"
```

Similar conditions can be used for RHEL and SUSE:


```
when: ansible_facts["os_family"] == "RedHat"
```


```
when: ansible_facts["os_family"] == "Suse"
```

Ansible gathers facts about each managed node and evaluates the condition before executing the task.

Step 4: Verify execution

Inspect the play recap after running each playbook. Confirm that tasks run only on the intended hosts and that skipped tasks are reported appropriately.

If a newly launched EC2 instance reports Host key verification failed, verify its SSH host key and update the master's known_hosts file before retrying.

## Attachments

- [screenshot-2026-10-22_16-00-40.png](attachments/screenshot-2026-10-22_16-00-40.png)
- [screenshot-2026-10-22_16-01-32.png](attachments/screenshot-2026-10-22_16-01-32.png)
- [screenshot-2026-10-22_18-12-20.png](attachments/screenshot-2026-10-22_18-12-20.png)

# KAN-142: Day 6 | Task 2 | Check Machine capacity and application health

- **Jira:** https://sasidharana504.atlassian.net/browse/KAN-142
- **Status:** Done
- **Assignee:** Mithun.U
- **Issue type:** Task
- **Priority:** Medium
- **Resolution:** Done
- **Reporter:** Mithun.U
- **Created:** 2026-10-21T04:37:02.953Z
- **Updated:** 2026-10-21T07:12:49.295Z
- **Due date:** —
- **Labels:** —
- **Components:** —

## Description

Objective: Assess CPU, memory, disk space, network ports, and Nginx/application health before deployment.

Steps: 

(1) Connect to the assigned Linux host.

 (2) Identify the OS.

 (3) inspect disk, memory, and running processes.

 (4) Install Nginx. 

(5) Validate its configuration and service. 

(6) Check port 80 and HTTP response.

 (7) Inspect logs.

 (8) Record findings.

cat /etc/os-release
lsb_release -a   # if installed
df -h
free -h
top
sudo apt update && sudo apt install nginx -y
sudo nginx -t
sudo systemctl status nginx
sudo ss -lntp | grep ':80'
curl -s -o /dev/null -w '%{http_code}\n' http://localhost

Log checks on systemd systems:

sudo journalctl -u nginx -n 50
sudo ls -lh /var/log/nginx/
sudo tail -20 /var/log/nginx/access.log

OS-specific note: 

Ubuntu/Debian package and systemd commands are normally available.

Expected outcome: OS and resource information recorded; Nginx configuration and service checked; port 80 and HTTP response tested; logs inspected; health-check report attached.

## Attachments

- [production_readiness_checklist_filled.xlsx](attachments/production_readiness_checklist_filled.xlsx)

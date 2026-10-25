# CNC-32: Day 9| Task 1 |Ten linux commands

- **Jira:** https://mail4mithunu.atlassian.net/browse/CNC-32
- **Status:** To Do
- **Assignee:** Mithun.U
- **Issue type:** Task
- **Priority:** Medium
- **Resolution:** —
- **Reporter:** Poojaharini K
- **Created:** 2026-10-25T16:00:47.276Z
- **Updated:** 2026-10-25T18:04:44.445Z
- **Due date:** —
- **Labels:** —
- **Components:** —

## Description

Commands

1. stat — Display detailed metadata about a file or directory, including permissions, ownership, size, and timestamps.   ``` stat /etc/hostname ```
2. file — Identify a file's type by examining its contents rather than relying only on its extension.   ``` file /bin/bash ```
3. findmnt — Display mounted filesystems and their mount points.   ``` findmnt ```
4. lsblk — List block devices and display information about disks, partitions, and their mount points.   ``` lsblk -f ```
5. lsof — List open files and identify the processes using them. (Use if already installed.)   ``` lsof /etc/hostname ```
6. fuser — Identify processes currently using a specified file or filesystem.   ``` fuser -v / ```
7. getent — Query system databases such as users, groups, and hostname mappings.   ``` getent passwd ```
8. namei — Trace a path component by component and display permissions along the path.   ``` namei -l /etc/hostname ```
9. column — Format input text into aligned columns for easier reading.   ``` printf 'Name:Age\nMithun:22\nAlex:25\n' | column -t -s ':' ```
10. timeout — Run a command with a time limit and terminate it if the limit is exceeded.   ``` timeout 3s sleep 10 ```

## Attachments

- [screenshot-2026-10-25_23-32-27.png](attachments/screenshot-2026-10-25_23-32-27.png)
- [screenshot-2026-10-25_23-33-06.png](attachments/screenshot-2026-10-25_23-33-06.png)
- [screenshot-2026-10-25_23-33-44.png](attachments/screenshot-2026-10-25_23-33-44.png)
- [screenshot-2026-10-25_23-34-37.png](attachments/screenshot-2026-10-25_23-34-37.png)

# KAN-45: Day-2-Infra Task 2 (Linux Filesystem Permissions) - Mithun

- **Jira:** https://sasidharana504.atlassian.net/browse/KAN-45
- **Status:** Done
- **Assignee:** Mithun.U
- **Issue type:** Task
- **Priority:** Medium
- **Resolution:** Done
- **Reporter:** Mithun.U
- **Created:** 2026-10-12T10:30:10.224Z
- **Updated:** 2026-10-12T13:08:35.761Z
- **Due date:** —
- **Labels:** —
- **Components:** —

## Description

Description: Proper access control is the backbone of Linux security. Today's mission is to move beyond basic chmod +x and master symbolic modes, octal values, ownership manipulation.

Set up a practice directory (mkdir perm_sandbox && cd perm_sandbox) and work through the following 5 core concepts and commands.

1. Inspecting Detailed Permission Structures (ls -l & stat)

- Concept: Unpack the 10-character permission string (-rwxr-xr-x) and inode metadata.
- Practice: Create a test file (touch test.txt) and run ls -l test.txt and stat test.txt.
- Deep-Dive: Understand the segments: File type (- for file, d for directory), Owner (u), Group (g), and Others (o).
2. Symbolic Mode Modification (chmod u=rwx,g=rx,o=r)

- Concept: Modify permissions explicitly using letters (u, g, o, a) and operators (+, -, =).
- Practice:  - Grant execute permission to everyone: chmod a+x test.txt - Remove write access for others: chmod o-w test.txt - Set exact permissions for owner only: chmod u=rw,g=,o= test.txt
3. Octal / Numeric Mode (Base-8 Permissions: 775, 644)

- Concept: Use numeric representations where Read = 4, Write = 2, and Execute = 1.
- Practice:  - Apply standard secure file permissions (rw-r--r--): chmod 644 test.txt - Apply standard secure directory permissions (rwxr-xr-x): chmod 755 . - Apply restricted private permissions (rwx------): chmod 700 test.txt
4. Recursive Permission Enforcement (chmod -R)

- Concept: Apply permission changes recursively down an entire directory tree.
- Practice: Create a nested structure (mkdir -p a/b/c && touch a/b/c/file.txt), then lock down the tree: chmod -R 750 a/.
5. Ownership and Group Reassignment (chown & chgrp)

- Concept: Manage who owns the file and which secondary group has access rights.
- Practice:  - Change file owner: sudo chown $USER test.txt - Change owner and group simultaneously: sudo chown $USER:$USER test.txt - Change group only: sudo chgrp adm test.txt

## Attachments

- [screenshot-2026-10-12_16-03-37.png](attachments/screenshot-2026-10-12_16-03-37.png)
- [screenshot-2026-10-12_16-04-52.png](attachments/screenshot-2026-10-12_16-04-52.png)
- [screenshot-2026-10-12_16-07-00.png](attachments/screenshot-2026-10-12_16-07-00.png)
- [screenshot-2026-10-12_16-10-22.png](attachments/screenshot-2026-10-12_16-10-22.png)

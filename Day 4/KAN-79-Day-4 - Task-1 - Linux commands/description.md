# KAN-79: Day-4 | Task-1 | Linux commands

- **Jira:** https://sasidharana504.atlassian.net/browse/KAN-79
- **Status:** Done
- **Assignee:** Mithun.U
- **Issue type:** Task
- **Priority:** Medium
- **Resolution:** Done
- **Reporter:** Mithun.U
- **Created:** 2026-10-14T09:35:08.078Z
- **Updated:** 2026-10-14T10:20:39.841Z
- **Due date:** —
- **Labels:** —
- **Components:** —

## Description

Theme: Process Management & Linux Administration

Today's commands focus on managing processes, inspecting resource usage, monitoring open files, checking user identities, and understanding process signals.

Today's Toolkit

1. pgrep -a bash — Find running Bash processes and display their process IDs and command lines.
2. pstree -p — Display running processes in a tree structure with their PIDs.
3. vmstat 1 5 — Monitor memory, CPU activity, processes, and I/O statistics over five intervals.
4. iostat -xz 1 3 — Inspect CPU and detailed disk I/O performance statistics. (Install sysstat if unavailable.)
5. lsof +D /tmp — List open files under /tmp and identify which processes are using them.
6. fuser -v /tmp — Identify processes accessing the /tmp directory.
7. id — Display your user ID, primary group, and supplementary group memberships.
8. getent passwd — Query the system's configured user account database.
9. systemctl --failed — List systemd units currently in a failed state.
10. kill -l — Display the signal names and numbers supported by your system.
Notes

- iostat and lsof may require installing packages such as sysstat and lsof.
- lsof +D /tmp can take some time if the directory contains many files.
- These commands are primarily diagnostic and do not intentionally modify system configuration or terminate processes.

## Attachments

- [screenshot-2026-10-14_15-47-02.png](attachments/screenshot-2026-10-14_15-47-02.png)
- [screenshot-2026-10-14_15-47-25.png](attachments/screenshot-2026-10-14_15-47-25.png)
- [screenshot-2026-10-14_15-49-06.png](attachments/screenshot-2026-10-14_15-49-06.png)
- [screenshot-2026-10-14_15-49-34.png](attachments/screenshot-2026-10-14_15-49-34.png)
- [screenshot-2026-10-14_15-50-28.png](attachments/screenshot-2026-10-14_15-50-28.png)

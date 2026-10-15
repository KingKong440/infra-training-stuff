# KAN-104: DAY-5 |TASK -1 | LINUX COMMANDS

- **Jira:** https://sasidharana504.atlassian.net/browse/KAN-104
- **Status:** Done
- **Assignee:** Mithun.U
- **Issue type:** Task
- **Priority:** Medium
- **Resolution:** Done
- **Reporter:** Mithun.U
- **Created:** 2026-10-15T07:15:39.776Z
- **Updated:** 2026-10-15T11:56:22.855Z
- **Due date:** —
- **Labels:** —
- **Components:** —

## Description

These are the common commands they should know and use during implementation.

Task Title: Learn and Practise 10 New Linux Commands

Description:

Research and practise 10 Linux commands that are not commonly used in daily work. Understand their syntax, options, use cases, and practical applications in system administration and troubleshooting.




```
# 1. Find all .log files
find /var/log -type f -name "*.log" 2>/dev/null

# 2. Search logs for errors
grep -in "error" application.log

# 3. Display the first column of a file
awk '{print $1}' data.txt

# 4. Replace text in a file's output
sed 's/ERROR/WARNING/g' application.log

# 5. Process a list of files
printf '%s\n' *.log | xargs -r grep -n "failed"

# 6. Create a compressed archive
tar -czf logs.tar.gz logs/

# 7. Find large directories
du -sh /var/log/* 2>/dev/null

# 8. Check which process uses port 8080
lsof -i :8080

# 9. View recent system logs
journalctl -n 50

# 10. Monitor memory usage every 2 seconds
watch -n 2 free -h
```

## Attachments

- [screenshot-2026-10-15_13-27-11.png](attachments/screenshot-2026-10-15_13-27-11.png)
- [screenshot-2026-10-15_13-29-19.png](attachments/screenshot-2026-10-15_13-29-19.png)
- [screenshot-2026-10-15_13-29-41.png](attachments/screenshot-2026-10-15_13-29-41.png)
- [screenshot-2026-10-15_13-30-04.png](attachments/screenshot-2026-10-15_13-30-04.png)

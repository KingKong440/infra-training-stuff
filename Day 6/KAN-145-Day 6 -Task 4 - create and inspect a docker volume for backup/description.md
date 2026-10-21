# KAN-145: Day 6 |Task 4 | create and inspect a docker volume for backup

- **Jira:** https://sasidharana504.atlassian.net/browse/KAN-145
- **Status:** Done
- **Assignee:** Mithun.U
- **Issue type:** Task
- **Priority:** Medium
- **Resolution:** Done
- **Reporter:** Mithun.U
- **Created:** 2026-10-21T04:39:04.092Z
- **Updated:** 2026-10-21T07:13:02.496Z
- **Due date:** —
- **Labels:** —
- **Components:** —

## Description

Objective: Create a named volume and prove that data remains available after the original container is deleted.

docker volume create my-vol
docker volume ls
docker inspect my-vol
docker inspect -f "{{ .Mountpoint }}" my-vol

Mount the volume in an Ubuntu container:

docker run -dit --name backup-container --mount source=my-vol,target=/data ubuntu:22.04
docker exec backup-container bash -c 'echo "Docker volume backup test" > /data/samplefile'
docker exec backup-container ls -l /data
docker exec backup-container cat /data/samplefile

Remove the container but retain the volume, then attach it to a new container:

docker rm -f backup-container
docker run -dit --name backup-container-2 --mount source=my-vol,target=/data ubuntu:22.04
docker exec backup-container-2 cat /data/samplefile

Expected outcome: Volume is created and inspected, sample file is readable, and its contents remain after container recreation. Do not delete my-vol during the test.

## Attachments

- [Pasted image.png](attachments/Pasted%20image.png)
- [Pasted image (2).png](attachments/Pasted%20image%20(2).png)

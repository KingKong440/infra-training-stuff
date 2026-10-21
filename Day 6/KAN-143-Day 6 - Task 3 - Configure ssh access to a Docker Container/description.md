# KAN-143: Day 6 | Task 3 | Configure ssh access to a Docker Container

- **Jira:** https://sasidharana504.atlassian.net/browse/KAN-143
- **Status:** Done
- **Assignee:** Mithun.U
- **Issue type:** Task
- **Priority:** Medium
- **Resolution:** Done
- **Reporter:** Mithun.U
- **Created:** 2026-10-21T04:37:31.198Z
- **Updated:** 2026-10-21T07:12:54.509Z
- **Due date:** —
- **Labels:** —
- **Components:** —

## Description

Objective: Build an SSH-enabled image and connect to a container through host port 2323 mapped to container port 22.

Steps: 

(1) Verify the approved Docker-compatible runtime.

 (2) Create a build directory and Dockerfile. 

(3) Build and run the image. 

(4) Configure SSH key authentication and restricted inbound access. 

(5) Connect to the container and verify logs.

mkdir -p dev && cd dev
vi Dockerfile

Use this safer lab Dockerfile as a starting point. Configure the developer public key in authorized_keys with correct ownership and permissions before connecting.

FROM ubuntu:22.04
RUN apt-get update && apt-get install -y openssh-server && \
    mkdir -p /run/sshd && useradd -m developer && \
    mkdir -p /home/developer/.ssh && \
    chown -R developer:developer /home/developer/.ssh && \
    rm -rf /var/lib/apt/lists/*
EXPOSE 22
CMD ["/usr/sbin/sshd", "-D"]

docker build -t sshdimage:v1.0 .
docker images
docker run -d --name sshcontainer -p 2323:22 sshdimage:v1.0
docker ps
docker logs sshcontainer

After configuring the public key:

ssh -p 2323 developer@EC2_PUBLIC_IP
docker exec -it sshcontainer bash

Expected outcome: Image builds, container runs, port mapping is verified, and SSH reaches the container. Restrict inbound TCP 2323 to a trusted IP. Do not expose root/password SSH login or hard-coded credentials.

## Attachments

- [Pasted image.png](attachments/Pasted%20image.png)
- [Pasted image (2).png](attachments/Pasted%20image%20(2).png)
- [Pasted image (3).png](attachments/Pasted%20image%20(3).png)

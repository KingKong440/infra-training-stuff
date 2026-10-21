# KAN-144: Day 6|Task 5 | build a custom docker image and push it to docker hub

- **Jira:** https://sasidharana504.atlassian.net/browse/KAN-144
- **Status:** Done
- **Assignee:** Mithun.U
- **Issue type:** Task
- **Priority:** Medium
- **Resolution:** Done
- **Reporter:** Mithun.U
- **Created:** 2026-10-21T04:38:08.516Z
- **Updated:** 2026-10-21T07:12:58.877Z
- **Due date:** —
- **Labels:** —
- **Components:** —

## Description

Objective: Build, tag, publish, and pull a custom image.

mkdir -p custom-image && cd custom-image
vi Dockerfile

Dockerfile:

FROM ubuntu:22.04
RUN apt-get update && apt-get install -y curl vim && \
    rm -rf /var/lib/apt/lists/*
CMD ["bash"]

docker build -t my-custom-image:v1.0 .
docker images
docker login
docker tag my-custom-image:v1.0 YOUR_DOCKERHUB_USERNAME/my-custom-image:v1.0
docker push YOUR_DOCKERHUB_USERNAME/my-custom-image:v1.0
docker pull YOUR_DOCKERHUB_USERNAME/my-custom-image:v1.0
docker images

Replace YOUR_DOCKERHUB_USERNAME with the actual account name. Use a personal access token if required. Never place passwords, tokens, or private keys in an image or screenshot.

Expected outcome: Custom image is built, tagged, pushed, and pulled successfully. Attach the repository URL and evidence.

## Attachments

- [Pasted image.png](attachments/Pasted%20image.png)
- [Pasted image (2).png](attachments/Pasted%20image%20(2).png)

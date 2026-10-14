# KAN-82: Day-4 | Task-3 | Create and Update a Dockerfile

- **Jira:** https://sasidharana504.atlassian.net/browse/KAN-82
- **Status:** Done
- **Assignee:** Mithun.U
- **Issue type:** Task
- **Priority:** Medium
- **Resolution:** Done
- **Reporter:** Mithun.U
- **Created:** 2026-10-14T09:45:43.488Z
- **Updated:** 2026-10-14T10:07:15.061Z
- **Due date:** —
- **Labels:** —
- **Components:** —

## Description

Create a Dockerfile based on Ubuntu that installs vim, wget, and unzip. Then modify the Dockerfile to remove unzip and install PHP CLI. Build separate image versions and verify the installed utilities.

Part 1: Create the Initial Dockerfile

Create a file named Dockerfile with the following content:


```
FROM ubuntu:24.04

RUN apt-get update && apt-get install -y vim wget unzip \
    && rm -rf /var/lib/apt/lists/*

CMD ["bash"]
```

Build the image:


```
docker build -t custom-ubuntu:v1 .
```

Run the container:


```
docker run -it --name ubuntu-v1 custom-ubuntu:v1
```

Verify the installed utilities:


```
vim --version
wget --version
unzip -v
```

Exit the container:


```
exit
```

Part 2: Modify the Dockerfile

Update the Dockerfile by removing unzip and installing php-cli.


```
FROM ubuntu:24.04

RUN apt-get update && apt-get install -y vim wget php-cli \
    && rm -rf /var/lib/apt/lists/*

CMD ["bash"]
```

Build the updated image:


```
docker build -t custom-ubuntu:v2 .
```

Run the updated container:


```
docker run -it --name ubuntu-v2 custom-ubuntu:v2
```

Verify the installed utilities:


```
vim --version
wget --version
php --version
command -v unzip
```

The final command should produce no output if unzip is not installed.

Exit the container:


```
exit
```

Acceptance Criteria

- Create a valid Dockerfile based on Ubuntu 24.04.
- Build the initial image with vim, wget, and unzip.
- Verify that all three utilities are installed.
- Modify the Dockerfile to remove unzip and install php-cli.
- Build the updated image using a new tag.
- Verify that vim, wget, and PHP are available in the updated container.
- Confirm that unzip is no longer installed.
- Capture screenshots of both Dockerfile versions, build outputs, and verification commands.
Cleanup

Remove the containers and custom images after capturing screenshots.


```
docker rm -f ubuntu-v1 ubuntu-v2
docker rmi custom-ubuntu:v1 custom-ubuntu:v2
```

Verify cleanup:


```
docker ps -a
docker images
```

Notes

- Run all build commands from the directory containing the Dockerfile.
- Rebuild the image after editing the Dockerfile; do not manually install packages inside a running container.
- Use separate image tags (v1 and v2) to distinguish the two versions.

## Attachments

- [screenshot-2026-10-14_15-23-38.png](attachments/screenshot-2026-10-14_15-23-38.png)
- [screenshot-2026-10-14_15-24-42.png](attachments/screenshot-2026-10-14_15-24-42.png)
- [screenshot-2026-10-14_15-28-12.png](attachments/screenshot-2026-10-14_15-28-12.png)
- [screenshot-2026-10-14_15-31-07.png](attachments/screenshot-2026-10-14_15-31-07.png)
- [screenshot-2026-10-14_15-31-59.png](attachments/screenshot-2026-10-14_15-31-59.png)
- [screenshot-2026-10-14_15-33-57.png](attachments/screenshot-2026-10-14_15-33-57.png)

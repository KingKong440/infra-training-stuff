# KAN-81: Day-4 | Task-2 | Pull and Run WordPress and MySQL Containers

- **Jira:** https://sasidharana504.atlassian.net/browse/KAN-81
- **Status:** Done
- **Assignee:** Mithun.U
- **Issue type:** Task
- **Priority:** Medium
- **Resolution:** Done
- **Reporter:** Mithun.U
- **Created:** 2026-10-14T09:44:37.397Z
- **Updated:** 2026-10-14T10:16:21.050Z
- **Due date:** —
- **Labels:** —
- **Components:** —

## Description

Pull the WordPress and MySQL images from Docker Hub and run both containers. Configure them to communicate using a Docker network and verify that WordPress is accessible locally.

Commands

1. docker pull wordpress — Download the WordPress image.
2. docker pull mysql:8.4 — Download the MySQL image.
3. docker images — Verify that both images are downloaded.
4. docker network create wp-network — Create a network for container communication.
5. Run the MySQL container:   ``` docker run -d --name mysql --network wp-network \   -e MYSQL_ROOT_PASSWORD=root123 \   -e MYSQL_DATABASE=wordpress \   -e MYSQL_USER=wpuser \   -e MYSQL_PASSWORD=wp123 \   mysql:8.4 ```
6. Run the WordPress container:   ``` docker run -d --name wordpress --network wp-network \   -p 8080:80 \   -e WORDPRESS_DB_HOST=mysql:3306 \   -e WORDPRESS_DB_USER=wpuser \   -e WORDPRESS_DB_PASSWORD=wp123 \   -e WORDPRESS_DB_NAME=wordpress \   wordpress ```
7. docker ps — Check whether both containers are running.
8. docker logs mysql — Inspect MySQL startup logs.
9. docker logs wordpress — Inspect WordPress logs.
10. Open http://localhost:8080 and verify that the WordPress setup page loads.
Acceptance Criteria

- Pull both Docker images successfully.
- Create a Docker network for communication between the containers.
- Run MySQL and WordPress containers with the required environment variables.
- Verify that both containers are running.
- Confirm that WordPress is accessible at http://localhost:8080.
- Capture screenshots of the images, containers, and WordPress page.
Cleanup

After completing the exercise and capturing screenshots, remove the containers, network, and downloaded images.


```
docker rm -f wordpress mysql
docker network rm wp-network
docker rmi wordpress mysql:8.4
```

Verify cleanup:


```
docker ps -a
docker images
docker network ls
```

Notes

- These credentials are for local practice only.
- Allow MySQL time to initialize before checking the WordPress page.
- No volume is required for this exercise; database data may be lost when the container is removed.

## Attachments

- [screenshot-2026-10-14_15-43-35.png](attachments/screenshot-2026-10-14_15-43-35.png)
- [screenshot-2026-10-14_15-44-56.png](attachments/screenshot-2026-10-14_15-44-56.png)
- [screenshot-2026-10-14_15-45-43.png](attachments/screenshot-2026-10-14_15-45-43.png)

# CNC-7: Day 7 | Task 4 | Mini Project: Jenkins GitHub Webhook Integration

- **Jira:** https://mail4mithunu.atlassian.net/browse/CNC-7
- **Status:** Done
- **Assignee:** Mithun.U
- **Issue type:** Task
- **Priority:** Medium
- **Resolution:** Done
- **Reporter:** Mithun.U
- **Created:** 2026-10-21T08:06:18.288Z
- **Updated:** 2026-10-21T11:56:46.081Z
- **Due date:** —
- **Labels:** —
- **Components:** —

## Description

Create a simple GitHub repository containing an index.html file and integrate it with Jenkins. Configure a GitHub webhook so that every push to the remote repository automatically triggers the corresponding Jenkins job.

Tasks

- Create a GitHub repository named jenkins-mini-project containing index.html.
- Create a Jenkins Freestyle project named github-integration.
- Configure Git SCM with the GitHub repository URL and target branch.
- Enable the GitHub hook trigger for GITScm polling option in Jenkins.
- Configure a GitHub webhook pointing to the Jenkins webhook endpoint.
- Set the webhook content type to application/json and enable push events.
- Verify that pushing a commit to the remote repository automatically triggers a Jenkins build.
Reference

- Jenkins installation: https://www.jenkins.io/download/
- GitHub webhook documentation: https://docs.github.com/en/webhooks

## Attachments

- [screenshot-2026-10-21_15-36-46.png](attachments/screenshot-2026-10-21_15-36-46.png)
- [screenshot-2026-10-21_15-38-43.png](attachments/screenshot-2026-10-21_15-38-43.png)
- [screenshot-2026-10-21_15-46-57.png](attachments/screenshot-2026-10-21_15-46-57.png)
- [screenshot-2026-10-21_15-47-23.png](attachments/screenshot-2026-10-21_15-47-23.png)
- [screenshot-2026-10-21_15-48-13.png](attachments/screenshot-2026-10-21_15-48-13.png)

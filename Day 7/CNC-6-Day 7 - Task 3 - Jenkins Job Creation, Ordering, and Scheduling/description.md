# CNC-6: Day 7 | Task 3 | Jenkins Job Creation, Ordering, and Scheduling

- **Jira:** https://mail4mithunu.atlassian.net/browse/CNC-6
- **Status:** Done
- **Assignee:** Mithun.U
- **Issue type:** Task
- **Priority:** Medium
- **Resolution:** Done
- **Reporter:** Mithun.U
- **Created:** 2026-10-21T08:02:37.286Z
- **Updated:** 2026-10-21T11:55:57.343Z
- **Due date:** —
- **Labels:** —
- **Components:** —

## Description

Create three Jenkins jobs to implement a basic CI/CD workflow. Configure job dependencies to control execution order and set up scheduled execution using Jenkins build triggers.

Tasks

1. Create Jenkins Jobs

- build — Create a Freestyle project to simulate the build stage. Configure a build step to print a success message and simulate application compilation.
- test — Create a Freestyle project to simulate the testing stage. Configure a build step to print a success message and simulate running application tests.
- deploy — Create a Freestyle project to simulate the deployment stage. Configure a build step to print a success message and simulate application deployment.
2. Configure Job Ordering

- Configure test to trigger after build completes successfully.
- Configure deploy to trigger after test completes successfully.
- Verify that the execution sequence is build → test → deploy.
- Verify that downstream jobs do not execute when their upstream job fails.
3. Configure Job Scheduling

- Configure a scheduled build trigger for the build job using Jenkins cron syntax.
- Set a test schedule, such as H/5 * * * *, to run the job approximately every five minutes.
- Verify that the scheduled build starts automatically.
- Confirm that successful scheduled builds trigger the downstream jobs in the correct order.
4. Validate Job Execution

- Execute the build job manually and verify its console output.
- Verify that test starts automatically after a successful build.
- Verify that deploy starts automatically after a successful test.
- Review build history, timestamps, job statuses, and console logs.
- Test failure handling by making an upstream job fail and verifying that subsequent jobs are not triggered.
Acceptance Criteria

- Three Jenkins jobs exist.
- Each job executes its configured build steps successfully.
- Job dependencies enforce the sequence build → test → deploy.
- Scheduled execution is configured and verified.
- Downstream jobs are triggered only after their upstream jobs succeed.
- Execution history and console logs demonstrate successful ordering, scheduling, and failure handling.
Reference

- Jenkins documentation: https://www.jenkins.io/doc/

## Attachments

- [screenshot-2026-10-21_15-09-35.png](attachments/screenshot-2026-10-21_15-09-35.png)
- [screenshot-2026-10-21_15-11-14.png](attachments/screenshot-2026-10-21_15-11-14.png)
- [screenshot-2026-10-21_15-12-50.png](attachments/screenshot-2026-10-21_15-12-50.png)
- [screenshot-2026-10-21_15-15-18.png](attachments/screenshot-2026-10-21_15-15-18.png)

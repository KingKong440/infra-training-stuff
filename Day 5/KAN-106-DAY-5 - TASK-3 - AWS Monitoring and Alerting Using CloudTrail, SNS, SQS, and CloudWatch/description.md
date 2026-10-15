# KAN-106: DAY-5 | TASK-3 | AWS Monitoring and Alerting Using CloudTrail, SNS, SQS, and CloudWatch

- **Jira:** https://sasidharana504.atlassian.net/browse/KAN-106
- **Status:** Review
- **Assignee:** Mithun.U
- **Issue type:** Task
- **Priority:** Medium
- **Resolution:** —
- **Reporter:** Mithun.U
- **Created:** 2026-10-15T07:16:47.404Z
- **Updated:** 2026-10-15T07:44:48.193Z
- **Due date:** —
- **Labels:** —
- **Components:** —

## Description

Jira Task: AWS Monitoring and Alerting Using CloudTrail, SNS, SQS, and CloudWatch

Description

Implement an AWS monitoring and alerting solution to monitor CloudTrail events and EC2 CPU utilization. Configure SNS for email notifications, SQS for message handling, and CloudWatch alarms to detect threshold conditions.

Implementation Steps

Step 1: Configure CloudTrail

- Create or configure a CloudTrail trail.
- Enable logging and verify that AWS activity events are recorded.
- Identify the events that should trigger alerts.
Step 2: Configure SNS Email Notifications

- Create an SNS topic.
- Subscribe an email address to the topic.
- Confirm the email subscription.
- Verify notification delivery.
Step 3: Configure SQS

- Create an SQS queue.
- Configure the required IAM roles and resource policies.
- Connect the queue to SNS or the relevant event workflow.
- Verify that messages are delivered and can be retrieved.
Step 4: Configure CloudTrail Event Alerting

- Create an Amazon EventBridge rule to match the selected CloudTrail events.
- Configure SNS and/or SQS as the appropriate targets.
- Test the workflow and verify alert delivery.
Step 5: Configure EC2 CPU Monitoring

- Identify the EC2 instance to monitor.
- Verify that CPU utilization metrics are available in CloudWatch.
- Create a CloudWatch alarm for the CPUUtilization metric.
- Configure the threshold as >= 0% as specified in the requirement.
- Configure the alarm action to publish notifications to SNS.
Step 6: Validate the Complete Workflow

- Generate a test CloudTrail event.
- Verify the event alert and email notification.
- Verify SQS message delivery.
- Check EC2 CPU metrics and CloudWatch alarm state.
- Document the results with screenshots and command output.
Acceptance Criteria

- CloudTrail logging is enabled and verified.
- SNS email subscription is confirmed and notifications are received.
- SQS queue and required permissions are configured.
- Selected CloudTrail events trigger the configured alert workflow.
- EC2 CPU utilization is monitored through CloudWatch.
- CloudWatch alarm threshold and SNS notification action are configured and tested.
- Implementation evidence is attached to Jira.
Expected Deliverable

A working AWS monitoring and alerting workflow integrating CloudTrail, EventBridge, SNS, SQS, EC2, and CloudWatch.

## Attachments

- [screenshot-2026-10-15_12-54-06.png](attachments/screenshot-2026-10-15_12-54-06.png)
- [screenshot-2026-10-15_13-00-06.png](attachments/screenshot-2026-10-15_13-00-06.png)
- [screenshot-2026-10-15_13-09-09.png](attachments/screenshot-2026-10-15_13-09-09.png)
- [screenshot-2026-10-15_13-11-46.png](attachments/screenshot-2026-10-15_13-11-46.png)

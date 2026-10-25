# CNC-35: Day9| Task2 |AWS Elastic Beanstalk Blue-Green Deployment

- **Jira:** https://mail4mithunu.atlassian.net/browse/CNC-35
- **Status:** In Review
- **Assignee:** Mithun.U
- **Issue type:** Task
- **Priority:** Medium
- **Resolution:** —
- **Reporter:** Poojaharini K
- **Created:** 2026-10-25T16:17:53.292Z
- **Updated:** 2026-10-25T17:59:30.989Z
- **Due date:** —
- **Labels:** —
- **Components:** —

## Description

Implement a Blue-Green Deployment strategy using AWS Elastic Beanstalk to deploy and validate a Java web application on the Tomcat platform. Configure the required infrastructure, security settings, and Auto Scaling policies, then clone the existing environment to create a Green environment and switch traffic between the two environments using environment domain swapping.

The objective is to understand how Blue-Green Deployment enables safer releases, minimizes deployment downtime, and supports rollback by retaining the previous application environment.

Implementation Steps

1. Create the Elastic Beanstalk Application

- Open the AWS Elastic Beanstalk console and select the ap-southeast-2 (Sydney) region.
- Create an Elastic Beanstalk application named blue-green-app.
- Create the initial environment named Blue-green-app-env.
- Select the Tomcat platform with the Corretto Java runtime.
- Configure the environment as a load-balanced environment with an Application Load Balancer.
- Configure the EC2 instance type and select the required key pair.
2. Configure Environment Settings and Security

- Configure the required environment variables.
- Create or assign the Elastic Beanstalk service role.
- Configure the EC2 instance profile and required IAM permissions.
- Review service access, networking, and security group settings.
- Ensure the load balancer and EC2 instances have the required access for the application to run.
3. Configure Auto Scaling

- Configure the Auto Scaling group with a minimum of one instance and a maximum of two instances.
- Configure scaling policies based on network traffic or resource utilization.
- Set the metric, evaluation period, scaling thresholds, cooldown period, and scale-out/scale-in adjustments.
- Review the configuration to ensure that the environment can respond to changes in application traffic.
4. Deploy and Validate the Initial Application

- Deploy a sample Java WAR application from a trusted source.
- Verify that the deployment completes successfully.
- Open the environment URL and confirm that the application is accessible.
- Check the environment health and review the deployment events for errors.
- Record the initial environment URL and deployed application version.
5. Create the Green Environment

- Clone the existing Elastic Beanstalk environment.
- Name the cloned environment green-env.
- Verify that the cloned environment is provisioned with the required configuration.
- Wait until the Green environment reaches a healthy state.
- Deploy or verify the intended application version in the Green environment.
- Open the Green environment URL and confirm that the application works independently of the Blue environment.
6. Perform the Blue-Green Switch

- Confirm that both environments are healthy and accessible before switching traffic.
- In the Elastic Beanstalk console, select the Swap environment domain action.
- Swap the environment CNAMEs between Blue-green-app-env and green-env.
- Verify that the original production URL now routes to the environment that was previously Green.
- Confirm that the environment domain fields reflect the completed swap.
7. Validate the Deployment

- Open the production URL and verify that the intended application is served.
- Check both environments' health status and recent event logs.
- Confirm that the previous environment remains available for rollback.
- Validate that traffic can be switched back by performing another environment domain swap if required.
- Capture screenshots of the environment configuration, Auto Scaling settings, deployed application, environment health, and successful domain swap for documentation.
8. Cleanup

- Delete the application
- delete the s3 buckets

## Attachments

- [screenshot-2026-10-25_22-36-47.png](attachments/screenshot-2026-10-25_22-36-47.png)
- [screenshot-2026-10-25_22-37-01.png](attachments/screenshot-2026-10-25_22-37-01.png)
- [screenshot-2026-10-25_22-42-10.png](attachments/screenshot-2026-10-25_22-42-10.png)
- [screenshot-2026-10-25_22-47-27.png](attachments/screenshot-2026-10-25_22-47-27.png)
- [screenshot-2026-10-25_22-52-00.png](attachments/screenshot-2026-10-25_22-52-00.png)
- [screenshot-2026-10-25_22-52-08.png](attachments/screenshot-2026-10-25_22-52-08.png)
- [screenshot-2026-10-25_22-54-51.png](attachments/screenshot-2026-10-25_22-54-51.png)
- [screenshot-2026-10-25_23-03-00.png](attachments/screenshot-2026-10-25_23-03-00.png)
- [screenshot-2026-10-25_23-03-19.png](attachments/screenshot-2026-10-25_23-03-19.png)
- [screenshot-2026-10-25_23-04-34.png](attachments/screenshot-2026-10-25_23-04-34.png)
- [screenshot-2026-10-25_23-05-38.png](attachments/screenshot-2026-10-25_23-05-38.png)
- [screenshot-2026-10-25_23-16-58.png](attachments/screenshot-2026-10-25_23-16-58.png)
- [screenshot-2026-10-25_23-19-30.png](attachments/screenshot-2026-10-25_23-19-30.png)

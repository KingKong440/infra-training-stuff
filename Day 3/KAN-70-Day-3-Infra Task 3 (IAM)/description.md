# KAN-70: Day-3-Infra Task 3 (IAM)

- **Jira:** https://sasidharana504.atlassian.net/browse/KAN-70
- **Status:** Done
- **Assignee:** Mithun.U
- **Issue type:** Task
- **Priority:** Medium
- **Resolution:** Done
- **Reporter:** Mithun.U
- **Created:** 2026-10-13T10:37:20.999Z
- **Updated:** 2026-10-14T04:26:28.515Z
- **Due date:** —
- **Labels:** —
- **Components:** —

## Description

AWS IAM - Group Management, Policies, Roles & MFA 

Today’s task focuses on setting up IAM access control for a team of 4 members. Each member will create their own IAM group, add all 4 team members to that group, and configure specific policies, permissions, roles, and MFA.

Today’s Toolkit

1. IAM Group Creation - Each team member creates a separate group
1. IAM User Creation - Create 4 individual IAM users, one for each team member.
1. Group Membership - Each member adds all 4 IAM users to their own group.
1. Policy Creation - Each member creates a custom policy for a specific task, such as S3 read-only access, EC2 viewing, or CloudWatch log viewing.
1. Policy Assignment - Attach the custom policy to the corresponding group so all members of that group inherit its permissions.
1. Permission Verification - Test the assigned permissions and confirm that unauthorized actions are denied.
1. IAM Role Creation - Each member creates a role for a specific purpose:
- Member 1: S3AuditRole - Read-only access to S3.
- Member 2: EC2MonitorRole - View EC2 instances and their details.
- Member 3: CloudWatchReadRole - View CloudWatch metrics and logs.
- Member 4: BillingViewRole - View billing and cost information, with the required billing access configuration.
1. Role Trust Configuration - Configure each role’s trust policy to specify which authorized identities can assume it.
1. MFA Configuration - Enable MFA for each of the 4 IAM users using an authenticator app or supported security key.
10. Role & Security Testing - Verify group membership, policy permissions, role assumption, MFA status, and allowed or denied actions.

Acceptance Criteria

- Each of the 4 team members creates a separate IAM group.
- Each group contains all 4 team members.
- Each member creates and attaches a policy for their assigned task.
- Each member creates their designated IAM role with an appropriate trust policy and permissions policy.
- Verify that group permissions and role permissions work as intended.
- Enable MFA for all 4 users.
- Test authorized and unauthorized actions.

## Attachments

- [img.jpeg](attachments/img.jpeg)
- [img2.jpeg](attachments/img2.jpeg)
- [img3.jpeg](attachments/img3.jpeg)
- [img4.jpeg](attachments/img4.jpeg)
- [img5.jpeg](attachments/img5.jpeg)

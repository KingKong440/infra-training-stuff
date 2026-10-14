# KAN-51: Day-2-Infra Task 4 (EC2 instance creation)

- **Jira:** https://sasidharana504.atlassian.net/browse/KAN-51
- **Status:** Done
- **Assignee:** Mithun.U
- **Issue type:** Task
- **Priority:** Medium
- **Resolution:** Done
- **Reporter:** Mithun.U
- **Created:** 2026-10-12T10:42:00.545Z
- **Updated:** 2026-10-12T13:09:41.227Z
- **Due date:** —
- **Labels:** —
- **Components:** —

## Description

Description: As part of our cloud sandbox rollout, we need to spin up two virtual machines on AWS within the Free Tier limits:

1. Ubuntu 24.04 LTS (Linux environment)
2. Windows Server 2019 Base (Windows environment)
Follow the deployment checklist below to ensure proper security configurations (SSH key access for Linux, strict security group rules) while avoiding any surprise AWS charges.

Step 1: Resource & Free Tier Configuration Parameters

Ensure you stick to these parameters to stay fully inside Free Tier parameters:

- Region: Choose a single region (e.g., us-east-1 or ap-south-1) and keep both instances there.
- Instance Type: t3.small
- Storage: Cap the EBS General Purpose SSD (gp2/gp3) at 30 GB total across the instances.
Step 2: Launching Instance 1 — Ubuntu 24.04 LTS

1. Navigate to the AWS EC2 Console and click Launch Instance.
2. Name: team-ubuntu-sandbox
3. Application and OS Images (AMI): Search for and select Ubuntu 24.04 LTS (Ensure it has the Free tier eligible tag).
4. Instance Type: Select t3.small
5. Key Pair:  - Click Create new key pair. Name it ubuntu-aws-key, select RSA and .pem format. - Download and save it securely. Remember to run chmod 600 ubuntu-aws-key.pem locally before connecting!
6. Network Settings (Security Group):  - Create a new security group named ubuntu-sec-group. - Rule 1 (SSH): Type: SSH, Port: 22, Source: My IP (Never expose port 22 globally to 0.0.0.0/0).
Step 3: Launching Instance 2 — Windows Server 2019 Base

1. In the EC2 Console, click Launch Instance again.
2. Name: team-windows-sandbox
3. Application and OS Images (AMI): Select Microsoft Windows Server 2019 Base (Ensure it displays Free tier eligible).
4. Instance Type: Select t3.small
5. Key Pair: Create a new key pair named windows-aws-key (.pem format) and download it. (You will use this private key inside the AWS console to decrypt your initial Administrator password).
6. Network Settings (Security Group):  - Create a new security group named windows-sec-group. - Rule 1 (RDP): Type: RDP, Port: 3389, Source: My IP (Restrict remote desktop access strictly to your secure IP address).

## Attachments

- [screenshot-2026-10-12_16-24-40.png](attachments/screenshot-2026-10-12_16-24-40.png)
- [screenshot-2026-10-12_16-28-08.png](attachments/screenshot-2026-10-12_16-28-08.png)

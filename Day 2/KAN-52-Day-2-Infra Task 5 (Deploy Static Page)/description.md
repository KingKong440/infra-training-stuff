# KAN-52: Day-2-Infra Task 5 (Deploy Static Page)

- **Jira:** https://sasidharana504.atlassian.net/browse/KAN-52
- **Status:** Done
- **Assignee:** Mithun.U
- **Issue type:** Task
- **Priority:** Medium
- **Resolution:** Done
- **Reporter:** Mithun.U
- **Created:** 2026-10-12T10:42:32.312Z
- **Updated:** 2026-10-12T13:09:59.407Z
- **Due date:** —
- **Labels:** —
- **Components:** —

## Description

Description: Now that our Ubuntu 24.04 and Windows Server 2019 instances are running, we need to spin up web servers on both machines and serve a custom static webpage to verify public network accessibility.

Part 1: Deploying httpd on Ubuntu

1. Connect to your Ubuntu instance via SSH:   ``` Bash ```   ``` chmod 600 ubuntu-aws-key.pem ssh -i "ubuntu-aws-key.pem" ubuntu@<UBUNTU_PUBLIC_IP> ```
2. Update repositories and install httpd:   ``` Bash ```   ``` sudo apt update && sudo apt install httpd -y ```
3. Enable and start the httpd service:   ``` Bash ```   ``` sudo systemctl enable httpd --now sudo systemctl status httpd ```
4. Update AWS Security Group:  - Go back to the AWS EC2 Console, edit your ubuntu-sec-group, and add an inbound rule: Type: HTTP, Port: 80, Source: 0.0.0.0/0 (or My IP for testing).
5. Deploy custom static content:  - Navigate to the default httpd web root directory (typically /var/www/html or /var/www/htdocs depending on the package variant):   ``` Bash ```   ``` cd /var/www/html ``` - Replace the default index page with your team custom message:   ``` Bash ```   ``` echo "<h1>Hello from Team Ubuntu httpd Sandbox! 🚀</h1>" | sudo tee index.html ```
6. Test: Open your browser and navigate to http://<UBUNTU_PUBLIC_IP>.
Part 2: Deploying IIS on Windows Server 2019

1. Connect to your Windows instance via RDP:  - In the AWS EC2 console, right-click team-windows-sandbox -> Connect -> RDP client. - Click Get password, upload your windows-aws-key.pem file to decrypt the Administrator password, and log in via Remote Desktop.
2. Install IIS (Internet Information Services):  - Open Server Manager inside Windows. - Click Add roles and features. - Navigate through the wizard until you reach Server Roles, and check the box for Web Server (IIS). - Proceed through the remaining steps with default settings and click Install.
3. Update AWS Security Group:  - Go to the AWS EC2 Console, edit your windows-sec-group, and add an inbound rule: Type: HTTP, Port: 80, Source: 0.0.0.0/0 (or My IP).
4. Deploy custom static content:  - Open PowerShell or File Explorer and navigate to the default IIS web root: C:\inetpub\wwwroot. - Open or create index.htm (or index.html), and replace the contents with:   ``` HTML ```   ``` <h1>Hello from Team Windows Server 2019 Sandbox! 🪟</h1> ``` - (Note: You may need to delete or rename the default iisstart.htm file so IIS prioritizes your custom index.htm file).
5. Test: Open your browser (locally or from your machine) and navigate to http://<WINDOWS_PUBLIC_IP>.

## Attachments

- [screenshot-2026-10-12_16-34-10.png](attachments/screenshot-2026-10-12_16-34-10.png)
- [screenshot-2026-10-12_17-39-39.png](attachments/screenshot-2026-10-12_17-39-39.png)

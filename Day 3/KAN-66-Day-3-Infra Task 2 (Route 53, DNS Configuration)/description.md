# KAN-66: Day-3-Infra Task 2 (Route 53, DNS Configuration)

- **Jira:** https://sasidharana504.atlassian.net/browse/KAN-66
- **Status:** Done
- **Assignee:** Mithun.U
- **Issue type:** Task
- **Priority:** Medium
- **Resolution:** Done
- **Reporter:** Mithun.U
- **Created:** 2026-10-13T09:17:57.372Z
- **Updated:** 2026-10-14T04:26:23.729Z
- **Due date:** —
- **Labels:** —
- **Components:** —

## Description

Theme: Domain Name & DNS Configuration with AWS Route 53 

Today’s task focuses on connecting a domain purchased through Hostinger to AWS Route 53, configuring DNS records, and verifying that the domain resolves to the correct IP address.

Today’s Toolkit

1. Domain Registration — Hostinger Obtain a domain name from Hostinger, or use an existing domain.
1. AWS Route 53 — Hosted Zone Creation: Create a public hosted zone in Route 53 using your registered domain name.
1. Name Server Configuration — Hostinger Copy the four name servers from the Route 53 hosted zone and update the domain’s nameserver settings in Hostinger.
1. DNS A Record — Route 53 Create an A record to point your domain to a server’s IPv4 address.
1. DNS CNAME Record — Route 53 Create a CNAME record to point www.yourdomain.com to your main domain.
1. DNS Configuration Check — Route 53 Verify that the required records are present and configured with the correct values.
1. DNS Resolution Test — Ubuntu Run nslookup yourdomain.com to check whether the domain resolves to the configured IP address.
1. DNS Lookup Test — Ubuntu Run dig yourdomain.com to inspect the DNS response and verify the record configuration.
1. Connectivity Test — Ubuntu Run ping -c 4 yourdomain.com to test connectivity, where ICMP traffic is allowed.
10. Website Response Test — Ubuntu Run curl -I http://yourdomain.com to check the HTTP response, if a web server is configured at the destination.

Simple Implementation Steps

Step 1: Create a hosted zone in Route 53

- Open AWS Console → Route 53.
- Go to Hosted zones → Create hosted zone.
- Enter your domain name, such as example.com.
- Select Public hosted zone and create it.
- Note the four NS (name server) values shown in the hosted zone.
Step 2: Update nameservers in Hostinger

- Log in to Hostinger and open Domains.
- Select your domain and find Nameservers.
- Choose the option to use custom nameservers.
- Replace the existing nameservers with the four NS values from Route 53.
- Save the changes.
After this, Route 53 becomes the authoritative DNS provider for the domain. DNS changes may take time to propagate.



Step 3: Create an A record in Route 53

- Open your hosted zone in Route 53.
- Select Create record.
- Record name: leave blank for the root domain.
- Record type: A.
- Value: enter your server’s public IPv4 address.
- Keep the default routing policy and create the record.
Example: example.com → 203.0.113.10 (documentation-only example IP).



Step 4: Create a CNAME record for www

- Select Create record again.
- Record name: www.
- Record type: CNAME.
- Value: example.com (your actual root domain).
- Create the record.
This maps www.example.com to example.com. You can skip this step if you don't need www.



Step 5: Verify from Ubuntu

Run these commands, replacing the example domain with yours:

Bash


```
nslookup example.com
dig example.com
dig www.example.com
```

Check that the returned IP address matches your A record and that the www name resolves correctly.

Acceptance Criteria

- Register or select an existing domain in Hostinger.
- Create a public hosted zone in AWS Route 53.
- Update Hostinger nameservers with the Route 53 NS values.
- Create an A record for the root domain.
- Create a CNAME record for www, if required.
- Verify DNS resolution using nslookup and dig.
- Capture screenshots of the hosted zone, nameserver configuration, DNS records, and terminal verification.
Important: You need a real server's public IP address to make the A record point to a working website. If you only want to practise DNS configuration, you can use a documentation IP for testing the record itself, but it will not host a reachable website. Once you change nameservers to Route 53, manage your DNS records there rather than in Hostinger's DNS zone.

## Attachments

- [screenshot-2026-10-13_15-18-28.png](attachments/screenshot-2026-10-13_15-18-28.png)
- [screenshot-2026-10-13_15-56-22.png](attachments/screenshot-2026-10-13_15-56-22.png)
- [screenshot-2026-10-13_15-56-50.png](attachments/screenshot-2026-10-13_15-56-50.png)

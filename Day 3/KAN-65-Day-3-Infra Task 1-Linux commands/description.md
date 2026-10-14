# KAN-65: Day-3-Infra Task 1-Linux commands

- **Jira:** https://sasidharana504.atlassian.net/browse/KAN-65
- **Status:** Done
- **Assignee:** Mithun.U
- **Issue type:** Task
- **Priority:** Medium
- **Resolution:** Done
- **Reporter:** Mithun.U
- **Created:** 2026-10-13T09:16:42.528Z
- **Updated:** 2026-10-14T04:26:20.697Z
- **Due date:** —
- **Labels:** —
- **Components:** —

## Description

Theme: Networking & Routing 

Today’s commands focus on understanding your network connection, checking IP addresses, inspecting routes, and testing connectivity. All commands are beginner-friendly and suitable for your Ubuntu terminal.

Today’s Toolkit

1. ip addr — Display network interfaces and their IP addresses.
1. ip route — View the routing table and identify the default gateway.
1. ping -c 4 google.com — Test internet connectivity by sending 4 packets.
1. ip link — Check network interfaces and whether they are up or down.
1. hostname -I — Display the IP addresses assigned to your machine.
1. ip neigh — View nearby devices discovered on the local network through ARP or Neighbor Discovery.
1. ss -tuln — List listening TCP and UDP ports.
1. traceroute google.com — Trace the network hops taken to reach a destination. (Install traceroute if it is missing.)
1. getent hosts google.com — Check whether a domain name resolves to an IP address.
10. curl -I https://google.com — Check HTTP response headers to test whether a website can be reached.

Acceptance Criteria

- Execute all 10 commands in your Ubuntu terminal.
- Observe and understand the output of each command.
- Capture screenshots showing the executed commands and their outputs.
Note: Some commands may behave differently depending on your network setup. If traceroute is unavailable, install it with sudo apt install traceroute. Commands such as ping and curl require network connectivity to produce meaningful results.

## Attachments

- [screenshot-2026-10-13_16-01-57.png](attachments/screenshot-2026-10-13_16-01-57.png)
- [screenshot-2026-10-13_16-03-04.png](attachments/screenshot-2026-10-13_16-03-04.png)
- [screenshot-2026-10-13_16-05-58.png](attachments/screenshot-2026-10-13_16-05-58.png)
- [screenshot-2026-10-13_16-06-31.png](attachments/screenshot-2026-10-13_16-06-31.png)

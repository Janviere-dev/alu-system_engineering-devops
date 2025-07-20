# Firewall Configuration: ALU System Engineering - DevOps

This directory contains configuration files and scripts related to setting up and managing firewall rules using `ufw` on `web-01`.

## 🔐 Task 0: Block All Incoming Traffic Except Mandatory Ports

- **Goal:** Restrict incoming traffic while allowing essential services: SSH (22), HTTP (80), and HTTPS (443).
- **Tool Used:** UFW (Uncomplicated Firewall)
- **File:** `0-block_all_incoming_traffic_but`
- **Details:**
  - Default incoming traffic: **denied**
  - Outgoing traffic: **allowed**
  - Allowed TCP ports: `22`, `80`, `443`

## 🔀 Task 100: Port Forwarding (Advanced)

- **Goal:** Redirect all traffic from port `8080` to port `80` where the Nginx web server is listening.
- **Tools Used:** UFW with iptables NAT configuration
- **File:** `100-port_forwarding`
- **Details:**
  - Edited `/etc/ufw/before.rules` to include NAT rule
  - Enabled IPv4 packet forwarding in `/etc/ufw/sysctl.conf`
  - Reloaded firewall to apply changes

## 🗂 Directory Structure



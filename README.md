# Firewall

🔒 Firewall Basics

🔹 What is a Firewall?

A firewall is a security system (software, hardware, or both) that controls incoming and outgoing network traffic based on predefined rules.
It acts as a barrier between trusted internal networks and untrusted external networks (like the internet).

🔹 Types of Firewalls

1.Packet-Filtering Firewall
  * Examines packets (source/destination IP, port, protocol).
  * Simple, fast, but limited — doesn’t look inside traffic.

2.Stateful Inspection Firewall
  * Tracks active connections and allows only valid return traffic.
  * More secure than packet filtering.

3.Application-Level Firewall (Proxy)
  * Filters traffic for specific applications (HTTP, FTP, DNS).
  * Can inspect content, not just headers.

4.Next-Generation Firewall (NGFW)
  * Includes deep packet inspection, intrusion prevention, malware detection.
  * Often used in enterprises.

🔹 Firewall Functions

  * Allow or block traffic based on rules (IP, port, protocol, program).
  * Protect against unauthorized access from external sources.
  * Limit exposure of vulnerable services (e.g., Telnet, FTP).
  * Segmentation of networks (internal vs. external).
  * Logging & monitoring of network activity.

🔹 Common Firewall Rules

  * Allow SSH (22) – so admins can connect.
  * Block Telnet (23) – insecure, often disabled.
  * Allow HTTP/HTTPS (80/443) – for web services.
  * Restrict access by IP range – e.g., only allow internal LAN.

🔹 Windows Firewall

  1. Open firewall configuration tool

   Press Win + R, type:

          wf.msc

   This opens Windows Defender Firewall with Advanced Security.

  2. List current firewall rules

   In the left pane, click Inbound Rules → you’ll see all rules.

  3. Add a rule to block inbound traffic on port 23 (Telnet)

   Click Inbound Rules → New Rule → Port
   Select TCP, enter 23, choose Block the connection, apply to all profiles.
   Name it: Block Telnet.

  4. Test the rule

   Open PowerShell:
      
      Test-NetConnection -Port 23 localhost
      
   It should show TcpTestSucceeded: False.

  5. Allow SSH (if using OpenSSH on Windows or Linux target)

   In Inbound Rules → New Rule → Port → TCP → 22
   Choose Allow the connection.

  6. Remove the test block rule

   Find Block Telnet in the list → Right-click → Delete.

Windows Firewall filters traffic by applying rule sets (allow/block) based on programs, ports, protocols, or IPs. Rules determine whether inbound/outbound         packets are passed or dropped.

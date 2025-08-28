Active Directory Lab – Initial Networking Setup
📌 Project Overview

Goal: Deploy 3 virtual machines on Vultr (2 Windows Server 2022 + 1 Ubuntu Splunk) with proper firewall rules and VPC networking. Configure networking so that all machines can communicate within the VPC.

Stack:

Windows Server 2022 (Domain Controller candidate)

Windows Server 2022 (Test machine)

Ubuntu (Splunk server)

Cloud Provider: Vultr (with Firewall Groups + VPC 2.0)

✅ Step 1: Deploy Virtual Machines

Provisioned 3 servers on Vultr:

Windows Server 2022 (Domain Controller)

Windows Server 2022 (Test Machine)

Ubuntu Server (Splunk)

Created a new Firewall Group with:

SSH (22) → My IP only

RDP (3389) → My IP only

Assigned Firewall Group to all servers.

Enabled VPC 2.0 for each VM.

Screenshots to include:

01-vultr-firewall.png – Firewall group with SSH + RDP rules

02-vpc-enabled.png – VPC enabled on servers

✅ Step 2: Verify Connectivity

RDP into Splunk server.

Tried to ping Test Server → result: Destination host unreachable.

RDP into Test Server and ran ipconfig.

Found 2 adapters:

Public IP address only

Missing expected VPC IP

Screenshots to include:

03-rdp-splunk.png – Logged into Splunk server

04-ping-fail.png – Failed ping attempt

05-ipconfig-test.png – Test server ipconfig output showing no VPC IP

✅ Step 3: Fix Networking

On Test Server → Network Settings → IPv4 Properties.

Changed from Automatic (DHCP) → Manual.

Input VPC IP address and Subnet Mask.

Re-tested ping from Splunk → Success.

Repeated the same static configuration for Domain Controller.

Screenshots to include:

06-manual-vpc-ip.png – Manual VPC IP + subnet mask configuration

07-ping-success.png – Successful ping from Splunk to Test Server

08-dc-ipconfig.png – Domain Controller showing VPC IP correctly

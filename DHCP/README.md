# DHCP Configuration Lab – Cisco Networking Project
## Overview

This project demonstrates the implementation and verification of the Dynamic Host Configuration Protocol (DHCP) in a Cisco networking environment.

The goal is to automate IPv4 address assignment to client devices, reduce manual configuration errors, and simplify network administration.

#Project Objectives
- Configure a Cisco router as a DHCP server.
- Create and manage DHCP address pools.
- Reserve critical IP addresses using excluded-address commands.
- Automatically assign network parameters to clients.
- Verify DHCP operation and troubleshoot potential issues.
- Network Services Provided
- IP Address Assignment
- Subnet Mask Distribution
-Default Gateway Configuration

## Technologies Used
- Cisco Packet Tracer
- DHCP
- IPv4 Addressing
- Basic Network Troubleshooting
  
Reserved specific IP addresses for infrastructure devices such as:
- Routers
- Switches

## Verification
The following commands were used to validate the DHCP deployment:

- show ip dhcp pool
- show ip dhcp binding
- show ip dhcp server statistics
- show running-config

Client-side verification:

- ipconfig /all
- ipconfig /renew
- 
Results
- Successful automatic IP address assignment

- Clients received correct network configuration

- End-to-end connectivity verified

- DHCP lease information successfully displayed

## Skills Demonstrated
- DHCP Deployment
- Cisco Router Configuration
- IP Address Management
- Network Troubleshooting
- Enterprise Network Fundamentals
- CCNA-Level Networking Concepts

  

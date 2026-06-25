# NAT & PAT Configuration Lab – Cisco Networking Project

## Overview
This project demonstrates the implementation of **Network Address Translation (NAT)** and **Port Address Translation (PAT)** on Cisco routers.

The objective is to enable devices using private IP addresses to communicate with external networks while conserving public IPv4 addresses and improving network scalability.

## Project Objectives
- Configure Static NAT for one-to-one address translation.
- Configure Dynamic NAT using a pool of public IP addresses.
- Configure PAT (NAT Overload) to allow multiple devices to share a single public IP address.
- Verify address translation and Internet connectivity.
- Understand how NAT and PAT support IPv4 address conservation.

## Key Concepts
- Private IP Addresses
- Public IP Addresses
- Static NAT
- Dynamic NAT
- PAT (NAT Overload)
- Address Translation Tables
- IPv4 Address Conservation

## Technologies Used
- Cisco Packet Tracer
- NAT
- PAT
- IPv4 Networking

## Configuration Highlights

### Static NAT

- Configured a permanent one-to-one mapping between a private host and a public IP address.
- Enabled external access to internal resources.

### Dynamic NAT

- Created a pool of public IP addresses.
- Configured automatic assignment of public addresses to internal hosts when needed.

### PAT (NAT Overload)

- Configured multiple internal devices to share a single public IP address.
- Used port numbers to distinguish simultaneous connections.

### Interface Roles
- Defined inside interfaces connected to the local network.
- Defined outside interfaces connected to the external network.

## Verification

The following commands were used to verify NAT and PAT operation:

```bash
show ip nat translations
show ip nat statistics
show running-config
```

Connectivity tests:

```bash
ping <destination-ip>
traceroute <destination-ip>
```

## Testing Scenarios

Static NAT Test:

* Verify that the internal server is reachable through its public IP address.

Dynamic NAT Test:

* Generate traffic from internal hosts.
* Confirm that addresses are assigned from the NAT pool.

PAT Test:

* Connect multiple hosts simultaneously.
* Verify that all hosts share the same public IP while using different port numbers.

## Results
- Static NAT successfully translated private addresses
- Dynamic NAT allocated public addresses from the configured pool
- PAT enabled multiple hosts to share a single public IP
-NAT translation entries successfully created
-End-to-end connectivity verified

## Skills Demonstrated
* NAT Configuration
* PAT (NAT Overload) Configuration
* Cisco Router Administration
* IP Address Management
* Network Troubleshooting
* Enterprise Network Fundamentals
* CCNA-Level Routing Concepts

## Learning Outcomes
Through this lab, I gained practical experience configuring and troubleshooting NAT and PAT, understanding the differences between Static NAT, Dynamic NAT, and PAT, and learning how address translation enables communication between private and public networks.

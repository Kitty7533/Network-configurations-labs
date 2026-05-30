# EIGRP Configuration Lab

## Overview
This lab focused on configuring EIGRP in a multi-router network. I assigned IP addresses, configured EIGRP, and verified network connectivity between all routers.

## Objectives
- Configure IP addressing on routers
- Enable and configure EIGRP
- Advertise network routes
- Verify EIGRP neighbor relationships
- Test end-to-end connectivity
- Network Topology


## Configuration Tasks
- Assigned IP addresses to router interfaces
- Configured EIGRP Autonomous System (AS)
- Advertised directly connected networks
- Verified EIGRP neighbors using the command ```Show Ip eigrp neighbors```
- Tested connectivity using ping
  
## What I Learned
During this lab, I learned:
- How EIGRP discovers neighboring routers
- How routes are exchanged automatically between routers
- The importance of correct IP addressing and subnetting
- How to verify EIGRP operation using show commands
- How EIGRP simplifies route management compared to static routing
  
## Commands Used
```bash
router eigrp 50
network 192.168.1.0
show ip eigrp neighbors
show ip route eigrp
show ip protocols
```

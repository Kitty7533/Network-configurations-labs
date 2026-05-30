# EtherChannel Configuration

## Overview
This lab focused on configuring EtherChannel to bundle multiple physical links into a single logical link between switches. The goal was to improve bandwidth and provide redundancy in the network.

## Objectives
- Configure switch interfaces for EtherChannel
- Understand link aggregation concepts
- Use LACP and PAgP protocols
- Verify EtherChannel status and operation
- Test network connectivity and redundancy

## Configuration Tasks
- Selected multiple physical links between switches
- Configured EtherChannel using LACP (or PAgP depending on your lab)
- Assigned interfaces to the same channel group
- Ensured trunk/access mode consistency on all bundled links
- Verified EtherChannel formation

## What I Learned
During this lab, I learned:
- How EtherChannel combines multiple links into one logical interface
- The importance of matching configurations on all participating ports
- The difference between LACP (open standard) and PAgP (Cisco proprietary)
- How EtherChannel improves bandwidth and provides redundancy
- How misconfiguration on one port can prevent channel formation

## Commands Used
```bash
interface range fa0/2-3
show etherchannel summary
show interface trunk
show ip interface fa0/2
channel-group 1 mode active
channel-group 1 mode passive
channel-group 1 mode desirable
channel-group 1 mode auto
```
## In result
* EtherChannel was successfully established between switches.
* Multiple physical links were bundled into a single logical connection.
* Network redundancy and bandwidth were improved.
* Traffic was distributed across active links.

## Personal Reflection
This lab helped me understand how real network infrastructures optimize performance and reliability. EtherChannel is very useful in enterprise networks because it prevents link overload and improves fault tolerance.

# VLAN Fundamentals

## Overview
This project demonstrates my understanding of VLANs (Virtual Local Area Networks), basics switch segmentation and the comprehension of VTP (Virtual Trunking Protocol) using Cisco Packet Tracer.

The goal of these labs is to separate devices into different logical networks while using th same physical switch.

## Objectives
- Create Vlans On a switch
- Assign switch ports to VLANs
- Verify VLAN communication
- Understand broadcast domain separation
- Understand how VTP works and how to configure it

## Technologies Used
- Cisco Packet Tracer
- Cisco switches
- VLAN configuration
- Basic Networs Concepts
- VTP configuration

## Topology
- Routers
- Switches
- PCs
- Different VLANs for different departments

## Configuration Steps

## 1.Create VLANS on switches
```bash
enable
configure terminal

hostname xxxx

vlan xx
name XX

do show vlan
```
## 2.Configure switch ports on Access or trunk depending to the situation
```bash
interface xxx
switchport mode access
switchport access vlan xx

interface xxxx
switchport mode trunk
end

show vlan
```

# What I learned
Through these labs, I understood:
- How VLANs improve network organization
- How switches separate broadcast domains
- Why VLANs increase security and performancee
- The difference between physical and logical segmentation









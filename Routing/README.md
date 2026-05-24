## Overview
This project demonstrates my understanding of basics routing  using Cisco Packet Tracer.

The goal of these labs is to improve routing configuration and troubleshooting skills for networking an cybersecurity environments.

## Objectives
- Create static routes
- Create dynamic routes
- Route advertisement
- Routing table verification
- Understand how equipments can communictate even if they are far from each other
- Understand basic RIP to EIGRP transition

## Technologies Used
- Cisco Packet Tracer
- Cisco switches
- Basic Networs Concepts
- RIP configuration
- EIGRPv6 configuration

## Topology
- Routers
- Switches
- PCs

## Configuration Steps

## 1.Basic configuration
```bash
enable
configure terminal

hostname xxxx

interface xxxxx
ip address xxxx
no shutdown

interface xxxxx
ipv6 address xxxxxx
no shutdown
```
## 2.Configure static and dynamic routes
```bash
Static route
ip route xxxxxx xxxxxx xxxxx(connected route,generic mask and next hop or exit interface)

RIPv1
router rip
network xxxx xxxx(connected route and generic mask)

RIPv2
router rip
version 2
network xxxx xxxx(connected route and generic mask)

RIPng
ipv6 unicast-routing
interface xxxxx
ipv6 rip xxxx enable(name)

EIGRPv6
ipv6 unicast-routing
ipv6 router eigrp xxxxx(as-number)
eigrp router-id xxxxxx(ipv4 address)
no shutdown
interface xxxxx
ipv6 eigrp xxxxx(As-number)
```
## 3.RIP to EIGRP transition
If RIP is already configure:
```bash
router RIP
distance 70
```
OR

```bash
ipv6 router eigrp xxxxx
distance 130
```

# What I learned
Through these labs, I understood:
- How equipmennts communicate even if they are far from each other
- How static and dynamic routes are configure
- The caracteristics of the different dynamic routing used here
- The difference between RIPv1 and RIPv2









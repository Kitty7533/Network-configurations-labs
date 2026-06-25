# OSPFv2 Configuration Lab – Cisco Networking Project

## Overview
This project demonstrates the implementation of **Open Shortest Path First Version 2 (OSPFv2)** in an IPv4 network environment.

The objective is to establish dynamic routing between multiple routers, enable automatic route learning, and ensure efficient path selection using OSPF's link-state routing mechanism.

## Project Objectives
- Configure OSPFv2 on Cisco routers.
- Establish OSPF neighbor adjacencies.
- Advertise networks dynamically.
- Verify the OSPF database and routing table.
- Analyze route propagation and path selection.

## Key Concepts
- Link-State Routing Protocol
- OSPF Areas
- Router ID
- Neighbor Adjacency
- Link-State Advertisements (LSAs)
- SPF (Shortest Path First) Algorithm
- Cost Metric
- Dynamic Routing

## Technologies Used
- Cisco Packet Tracer
- OSPFv2
- IPv4 Networking
- Routing and Switching

## Configuration Highlights

### OSPF Process Configuration
- Enabled OSPF routing on Cisco routers.
- Assigned a unique Router ID to each router.
- Configured OSPF process IDs.

### Network Advertisement
- Advertised directly connected networks using OSPF.
- Enabled route exchange between routers.
- Verified network reachability across the topology.

### Neighbor Relationship
- Established OSPF neighbor adjacencies.
- Confirmed successful exchange of routing information.
- Monitored OSPF state transitions.

### Route Learning
- Learned remote networks dynamically.
- Populated routing tables with OSPF routes.
- Verified optimal path selection based on OSPF cost.

## Verificatio
The following commands were used to verify OSPF operation:

```bash
show ip ospf neighbor
show ip ospf database
show ip protocols
show ip route ospf
show ip route
show running-config
```

Connectivity tests:

```bash
ping <destination-ip>
traceroute <destination-ip>
```

## Testing Scenarios

### Neighbor Adjacency Verification
* Verify routers successfully form OSPF neighbor relationships.
* Confirm Full adjacency state.

### Routing Table Verification
* Check that remote networks appear as OSPF routes.
* Verify correct next-hop information.

### End-to-End Connectivity
* Test communication between hosts located on different networks.
* Verify successful route propagation.

## Results
- OSPF neighbor adjacencies successfully established
- Routing information exchanged dynamically
- Remote networks learned automatically
- OSPF routes installed in routing tables
- End-to-end connectivity verified

## Skills Demonstrated
* Dynamic Routing Configuration
* OSPFv2 Deployment
* Cisco Router Administration
* Routing Troubleshooting
* Network Design and Optimization
* Link-State Routing Concepts
* CCNA Enterprise Networking Fundamentals

## Learning Outcomes
Through this lab, I gained practical experience configuring and troubleshooting OSPFv2, establishing neighbor relationships, analyzing the OSPF database, and understanding how dynamic routing protocols efficiently exchange routing information across enterprise networks.

## Advanced Concepts Explored
* Router ID election process
* OSPF Neighbor Discovery
* OSPF Adjacency Formation
* Link-State Database (LSDB)
* Designated Router (DR) and Backup Designated Router (BDR)
* OSPF Route Calculation using SPF Algorithm
* OSPF Troubleshooting using `show ip ospf neighbor` and `show ip ospf database`


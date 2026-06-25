# STP Configuration Lab – Cisco Networking Project

## Overview
This project demonstrates the implementation of the **Spanning Tree Protocol (STP)** in a switched network environment.

The topology contains redundant links between switches, which can potentially create Layer 2 loops. STP is used to prevent these loops by electing a Root Bridge and placing redundant links into a blocking state while maintaining network redundancy.

## Project Objectives
* Understand the purpose of Spanning Tree Protocol.
* Prevent Layer 2 switching loops.
* Analyze Root Bridge election.
* Identify Root Ports and Designated Ports.
* Observe blocked and forwarding ports.
* Verify network connectivity in a redundant topology.

## Topology Description
The lab consists of:

* 3 Cisco 2960 switches (S1, S2, S3)
* 2 PCs (PCA and PCB)
* Redundant links forming a triangular topology

This design intentionally introduces potential switching loops to demonstrate how STP maintains a loop-free network.

## Key Concepts
* Layer 2 Loop Prevention
* Root Bridge Election
* Root Port (RP)
* Designated Port (DP)
* Non-Designated Port
* Blocking State
* Forwarding State
* Network Redundancy

## Technologies Used
* Cisco Packet Tracer
* Cisco Catalyst 2960 Switches
* Spanning Tree Protocol (STP)
* Ethernet Switching

## Configuration Highlights

### STP Operation
* STP automatically elected a Root Bridge.
* Each non-root switch selected a Root Port.
* One redundant link was placed into a blocking state.
* A loop-free topology was established.

### Redundancy
* Physical redundancy was maintained.
* Backup paths remained available in case of link failure.

## Verification

The following commands were used to analyze STP behavior:

```bash
show spanning-tree
show spanning-tree vlan 1
show spanning-tree root
show running-config
```

## Testing Scenarios

### Root Bridge Election
* Determine which switch became the Root Bridge.
* Analyze Bridge ID and priority values.

### Port Role Analysis
* Root Ports
* Designated Ports
* Blocking Ports

### Failover Test
* Disconnect an active link.
* Observe STP recalculation.
* Verify restoration of connectivity through the backup path.

## Results
- Root Bridge successfully elected
- Layer 2 loops prevented
- Redundant topology maintained
- One link placed in blocking state
- Connectivity preserved between end devices
- Automatic failover achieved during link failure

## Skills Demonstrated
* Switching Fundamentals
* STP Configuration and Verification
* Layer 2 Troubleshooting
* Redundancy Implementation
* Cisco Catalyst Switch Administration
* Enterprise Campus Networking Concepts
* CCNA Switching Technologies

## Learning Outcomes
Through this lab, I gained practical experience understanding how STP prevents switching loops, elects a Root Bridge, manages redundant paths, and ensures network stability in Layer 2 environments.

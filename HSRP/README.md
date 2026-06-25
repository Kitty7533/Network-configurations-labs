# HSRP Configuration Lab – Cisco Networking Project

## Overview
This project demonstrates the implementation of the Hot Standby Router Protocol (HSRP) to provide gateway redundancy and improve network availability.

HSRP allows multiple routers to work together as a single virtual default gateway. If the active router fails, the standby router automatically takes over, ensuring minimal disruption for network users.

## Project Objectives
- Configure HSRP between two Cisco routers.
- Create a virtual default gateway for clients.
- Configure router priorities.
- Verify HSRP operation and redundancy mechanisms.
  
## Key Concepts
- First Hop Redundancy Protocol (FHRP)
- Active Router
- Standby Router
- Virtual IP Address
- Virtual MAC Address
- Gateway Redundancy
- High Availability
  
## Technologies Used
- Cisco Packet Tracer
- HSRP
- IPv4 Networking
- Network Redundancy
- HSRP Group Configuration
- Configured an HSRP group on both routers.
- Assigned a shared virtual IP address.
- Defined router priorities to determine the active router.
- Priority and Preemption
- Configured priority values to control active router election.
- Enabled preemption to allow the preferred router to regain active status after recovery.
- Default Gateway Redundancy
- Clients use the virtual IP as their default gateway.
- Traffic continues to flow even if the active router becomes unavailable.
  
##Verification

The following commands were used to verify HSRP operation:

- show standby brief
- show standby
- show running-config

Connectivity tests:
```
ping <destination-ip>
tracert <destination-ip>
```
- Failover Testing
- Verify Router 1 is the Active Router.
- Shutdown the active router interface.
- Confirm Router 2 becomes the Active Router.
- Test connectivity from client devices.
- Restore Router 1 and verify preemption behavior.
  
## Results
- successfully configured
- Virtual gateway operational
- Automatic failover achieved
- Network connectivity maintained during router failure
- Gateway redundancy verified

## Skills Demonstrated
- High Availability Configuration
- Gateway Redundancy Implementation
- HSRP Deployment
- Cisco Router Configuration
- Network Resilience and Fault Tolerance
- CCNA Enterprise Networking Fundamentals

  

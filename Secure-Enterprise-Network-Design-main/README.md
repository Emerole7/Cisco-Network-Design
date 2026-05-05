# Secure-Enterprise-Network-Design
This project presents the network design and implementation for CyberNet Ltd, a multi-branch organization requiring a scalable, secure, and highly available network infrastructure connecting headquarters and branch offices.

## Network Architecture
The design follows a three-tier hierarchical model:
- Core Layer
- Distribution Layer
- Access Layer
This improves:
- Performance
- Scalability
- Maintainability
## Key Security Features
- VLAN segmentation for department isolation
- SSH for secure remote management
- Cisco ASA Firewall (inside/outside security zones)
- ACLs controlling inter-network traffic
## Redundancy & High Availability
- Dual core switches for failover
- EtherChannel (LACP) for link aggregation
- Multiple uplinks between layers
- Elimination of single points of failure
## Routing & Switching
- Inter-VLAN Routing using SVIs
- OSPF for dynamic routing across the enterprise
- Static routes for edge connectivity
## Services Implemented
- DHCP (dynamic IP allocation)
- DNS (name resolution)
- Static IP allocation for servers
- Wireless Access Points per branch
## Technologies Used
- Cisco Packet Tracer
- Cisco IOS CLI
- VLANs, STP, EtherChannel
- OSPF routing protocol
- Cisco ASA Firewall

## Outcome
The final design ensures:
- Secure communication across all branches
- Scalable enterprise growth
- Reliable connectivity with redundancy
- Efficient traffic segmentation

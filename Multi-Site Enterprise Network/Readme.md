## TechCore Solutions - Enterprise Network design and implementation
This is a multi-site enterprise network featuring GRE tunneling, OSPF routing, VLAN segmentation, centralized services, and secure access control.

## Network Architecture
This design simulates a real-world Headquarters and Branch office environment, connected through an ISP via a GRE tunnel and OSPF Area 0. The topology implements enterprise-grade standards across all Layer 3 routing, NAT boundaries, DHCP services, VLAN segmentation, Access Control Lists, and network security configurations.

Headquarters:
The HQ site operates four VLANs, Management, Sales, Engineering, and Blackhole. 
Inter-VLAN routing is handled via Router-on-a-Stick on HQ-RTR. 
Layer 2 redundancy is achieved through EtherChannel using PAgP between HQ switches.
All internal hosts receive addressing and services from a centralized server running DHCP, DNS, TFTP, and HTTP. 
NAT Overload is configured on HQ-RTR to provide internet access for all internal networks.

Branch Office:
The Branch site hosts three VLANs, Admin, Guest, and Blackhole.   
Inter-VLAN routing is also configured via Router-on-a-Stick. 
Branch hosts obtain IP addressing through DHCP relay forwarded to the HQ server. 
All internet-bound traffic is routed through HQ's NAT boundary, and OSPF adjacency is maintained through the GRE tunnel.

ISP Router:
The ISP router simulates a public WAN segment and serves as the tunnel carrier connecting both the HQ and Branch sites across the simulated internet.

## Key Features

VLAN & Addressing:
Full VLSM subnetting is applied across all networks using the 192.168.99.0/24 address space. 
The GRE tunnel uses 192.168.98.0/30, and all VLANs are configured with the first usable address as the default gateway.

Access Control:
ACLs are applied inbound on sub-interfaces to enforce traffic policies. 
Sales and Engineering VLANs are blocked from communicating with each other in both directions. 
The Management VLAN retains full network access.
Additional ACLs restrict access to DNS and HTTP services.

Centralized Services:
The HQ server provides all network services including DHCP for both HQ and Branch VLANs, internal DNS resolution, TFTP for device configuration backups, and an internal HTTP web server.

Layer 2 configuration:
HQ-SW1 is configured as the STP root bridge for all VLANs. 
EtherChannel is established between HQ switches for redundancy and increased throughput. 
All unused switch interfaces are assigned to VLAN 99 and administratively shut down.

NAT & Internet Edge:
NAT Overload is configured exclusively on HQ-RTR. 
The ISP router provides the simulated public network, and the Branch office relies entirely on HQ as its NAT boundary for all outbound internet traffic.

Routing:
OSPF Area 0 is deployed across all three routers. 
The GRE tunnel provides a logical point-to-point adjacency between HQ and Branch, enabling a consistent and scalable single-area routing design.

Security:
All devices are hardened with SSH-only remote access and RSA key generation. 
Login and MOTD banners are configured network wide. 
Port security is enforced using sticky MAC addressing with a maximum of two addresses per port in restrict mode. 
CDP is disabled on all WAN-facing interfaces, and all passwords are encrypted.

## Summary
This lab successfully demonstrates the ability to plan, configure, and verify a complete enterprise network from the ground up, spanning Layer 2 switching, Layer 3 routing, WAN tunneling, centralized services, access control, and security hardening, producing a topology that mirrors the complexity and standards of a production network environment. 

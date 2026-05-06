## Network monitoring using Syslog and SNMP

This lab demonstrates the configuration and verification of Syslog and SNMP within a Cisco network environment to support centralized event logging, real-time monitoring, and remote device management. 
The lab implements Syslog and SNMP across both HQ and Branch routers, simulating enterprise-grade network administration practices.
The lab is structured into two part:

Part 1 – Syslog: Configuration and verification of centralized log collection
Part 2 – SNMP: Configuration and execution of remote management operation

## Network Addressing Summary
HQ LAN: 192.168.1.0/24
Branch LAN: 172.16.1.0/24
Syslog Server: 192.168.1.5 
SNMP Manager: Installed on PC 2 in the Branch LAN

## Part 1 - Syslog: Configuration and verification of centralized log collection
Syslog was configured on both the HQ and Branch routers to forward log messages to a centralized Syslog server residing on the HQ LAN.

Configuration
Both routers were configured with the following commands to enable remote logging:

- logging 192.168.1.5: directs log messages to the centralized Syslog server
- logging trap debugging: sets the minimum severity level to capture all log messages
- service timestamps log datetime msec: appends precise timestamps to each log entry

Verification
The Syslog configuration was verified using the show logging command on both routers, confirming the correct logging destination and active severity levels.

Log Generation Test
To validate end-to-end functionality, the Branch router's LAN interface was administratively shut down to trigger system-level events. The resulting log messages were successfully captured and recorded on the Syslog server, confirming that the configuration was operating as expected.

## Part 2 – SNMP: Configuration and execution of remote management operation
SNMP was configured on both routers to enable centralized monitoring and remote management via an SNMP Manager application.

SNMP Agent Configuration
SNMP agents were enabled on the HQ and Branch routers using the following commands:

- snmp-server community public ro : grants read-only access for monitoring operations
- snmp-server community private rw : grants read-write access for remote configuration changes

SNMP Operations
The following operations were performed using the SNMP Manager GUI on a PC2  within the Branch LAN:
- GET Request was used to query the Branch router (172.16.1.1) for system uptime by identifying the corresponding OID from the MIB browser
- SET Request was used to modify the Branch router's hostname remotely via SNMP from Branch-A to Router - Branch-A

## Key Learnings / Outcomes
This project demonstrates hands-on experience with enterprise network monitoring and device management.

- Centralized Log Management — Deployed and validated a Syslog architecture across multiple Cisco routers, enabling real-time event visibility from a single monitoring point
- SNMP Monitoring & Remote Management — Configured SNMP agents with tiered access controls and executed live GET/SET operations to retrieve device metrics and apply remote configuration changes
- Fault Detection & Verification — Simulated network events to confirm end-to-end Syslog delivery, reflecting real-world troubleshooting and validation workflows
- MIB & OID Proficiency — Navigated MIB trees to identify and query specific OIDs, demonstrating familiarity with SNMP data structures used in production monitoring environments
- Multi-Site Network Administration — Applied consistent monitoring configurations across HQ and Branch routers, simulating enterprise-scale network management practices

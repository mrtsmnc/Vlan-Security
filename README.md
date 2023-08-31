# Vlan-Security
Vlan Security

Packet Tracer - Layer 2 VLAN Security

Objectives

·         Connect a new redundant link between SW-1 and SW-2.
·         Enable trunking and configure security on the new trunk link between SW-1 and SW-2.
·         Create a new management VLAN (VLAN 20) and attach a management PC to that VLAN.
·         Implement an ACL to prevent outside users from accessing the management VLAN.

Background / Scenario

A company’s network is currently set up using two separate VLANs: VLAN 5 and VLAN 10. In addition, all trunk ports are configured with native VLAN 15. A network administrator wants to add a redundant link between switch SW-1 and SW-2. The link must have trunking enabled and all security requirements should be in place.

In addition, the network administrator wants to connect a management PC to switch SW-A. The administrator would like to enable the management PC to connect to all switches and the router, but does not want any other devices to connect to the management PC or the switches. The administrator would like to create a new VLAN 20 for management purposes.

All devices have been preconfigured with:

o    Enable secret password: ciscoenpa55
o    Console password: ciscoconpa55
o    SSH username and password: SSHadmin / ciscosshpa55

Part 1: Verify Connectivity
Step 1: Verify connectivity between C2 (VLAN 10) and C3 (VLAN 10).
Step 2: Verify connectivity between C2 (VLAN 10) and D1 (VLAN 5).

Note: If using the simple PDU GUI packet, be sure to ping twice to allow for ARP.

Part 2: Create a Redundant Link Between SW-1 and SW-2
Step 1: Connect SW-1 and SW-2.
Using a crossover cable, connect port F0/23 on SW-1 to port F0/23 on SW-2.
Step 2: Enable trunking, including all trunk security mechanisms on the link between SW-1 and SW-2.

Trunking has already been configured on all pre-existing trunk interfaces. The new link must be configured for trunking, including all trunk security mechanisms. On both SW-1 and SW-2, set the port to trunk, assign native VLAN 15 to the trunk port, and disable auto-negotiation.

Part 3: Enable VLAN 20 as a Management VLAN

The network administrator wants to access all switch and routing devices using a management PC. For security purposes, the administrator wants to ensure that all managed devices are on a separate VLAN.

Step 1: Enable a management VLAN (VLAN 20) on SW-A.
a.     Enable VLAN 20 on SW-A.
b.     Create an interface VLAN 20 and assign an IP address within the 192.168.20.0/24 network.

Step 2: Enable the same management VLAN on all other switches.
a.     Create the management VLAN on all switches: SW-B, SW-1, SW-2, and Central.
b.     Create an interface VLAN 20 on all switches and assign an IP address within the 192.168.20.0/24 network.

Step 3: Connect and configure the management PC.
Connect the management PC to SW-A port F0/1 and ensure that it is assigned an available IP address within the 192.168.20.0/24 network.

Step 4: On SW-A, ensure the management PC is part of VLAN 20.
Interface F0/1 must be part of VLAN 20.

Step 5: Verify connectivity of the management PC to all switches.
The management PC should be able to ping SW-A, SW-B, SW-1, SW-2, and Central.

Part 4: Enable the Management PC to Access Router R1

Step 1: Enable a new subinterface on router R1.

a.     Create subinterface g0/0.3 and set encapsulation to dot1q 20 to account for VLAN 20.
b.     Assign an IP address within the 192.168.20.0/24 network.

Step 2: Verify connectivity between the management PC and R1.
Be sure to configure the default gateway on the management PC to allow for connectivity.

Step 3: Enable security.
While the management PC must be able to access the router, no other PC should be able to access the management VLAN.
a.     Create an ACL that allows only the Management PC to access the router.
b.     Apply the ACL to the proper interface(s).

Note: There are multiple ways in which an ACL can be created to accomplish the necessary security. For this reason, grading on this portion of the activity is based on the correct connectivity requirements. The management PC must be able to connect to all switches and the router. All other PCs should not be able to connect to any devices within the management VLAN.

Step 4: Verify security.
a.     Verify only the Management PC can access the router. Use SSH to access R1 with username SSHadmin and password ciscosshpa55.
PC> ssh -l SSHadmin 192.168.20.100
b.     From the management PC, ping SW-A, SW-B, and R1. Were the pings successful? Explain.
c.     From D1, ping the management PC. Were the pings successful? Explain.

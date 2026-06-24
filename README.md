# inter-vlan-routing-lab
Project: Implementing Network Segmentation and Inter-VLAN Routing
📋 Project Overview
This project addresses the security risks of a flat network topology where different departments share the same broadcast domain. By implementing Layer 2 network segmentation using VLANs, the Sales and HR departments are isolated to prevent unauthorized data access and limit the blast radius of potential network threats. Inter-VLAN routing is configured via a Router-on-a-Stick architecture to allow controlled, secure communication between the segments.
🗺️ Network Topology
[<img width="1366" height="768" alt="my soho" src="https://github.com/user-attachments/assets/a2829df0-eca0-43bb-b160-16568d062f43" />
]
⚙️ Configuration Deployment
Switch Configuration:
vlan 10
 name Sales
vlan 20
 name HR
interface fastethernet 0/1
 switchport mode access
 switchport access vlan 10
interface fastethernet 0/3
 switchport mode access
 switchport access vlan 20
interface fastethernet 0/24
 switchport mode trunk
 Router Configuration:
 interface gigabitethernet 0/0.10
 encapsulation dot1Q 10
 ip address 192.168.10.1 255.255.255.0
interface gigabitethernet 0/0.20
 encapsulation dot1Q 20
 ip address 192.168.20.1 255.255.255.0
interface gigabitethernet 0/0
 no shutdown
 Verification & Testing
Run show vlan brief on the switch to verify VLAN ports.
Run show running-config and copy running-config startup-config to verify and save settings.
Run ping 192.168.20.2 from the Sales PC to confirm Inter-VLAN routing success.

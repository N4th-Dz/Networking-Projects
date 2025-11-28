<H1> HQ Site <> Branch Site Network Infrastructure </h1> 

#####################################################################################################################################################################################
This project simulates a complete enterprise network connecting two sites—HQ Office and Branch Office—through redundant ISP paths using redundant secure IPSec VPN tunnels. 
The Branch office hosts all critical network services (DNS, DHCP, WEB Servers), while both sites are designed for high availability, scalability, and secure communication.
######################################################################################################################################################################################

🛠️ Implemented Features and Technologies
1. Enterprise Network Architecture












🖥️ Network Devices Used 
Cisco ISR 4331 Routers:
  - HQ Core Router
  - Branch Core Router
  - ISP Main
  - ISP Backup

Cisco Catalyst 3650 L3 Switches:
  - Aggregate Multilayer Switches (HQ and Branch)

Cisco Catalyst 2960 L2 Switches
  - Access Switches (HQ and Branch)













<H2> Network Topology Overview </h2> 

⇆🌍 WAN Connection

Main Path: HQ Core Router <> ISP Main <> Branch Core Router
Redundant Path: HQ Core Router <> ISP Backup <> Branch Core Router

IPSec Site-to-Site VPN Tunnel: 
Main Tunnel: Via ISP Main 
Backup Tunnel: Via ISP Backup

🖧 LAN Connection (Internal Network)
- Heirarchical Design (Core <> Aggregate/Distribution <> Access)

HQ Office: 
- 3 Office Departments segmented by their respective VLANs
  - Customer Service Department
  - HR Department
  - Marketing Department
- Regular Users are being hosted

Branch Office: 
- Internal Servers are hosted (DNS, DHCP, WEB Server) 
- IT Department (Adminsitrators) and Security Department are hosted


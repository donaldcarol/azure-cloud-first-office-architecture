# Network Design



## 1. Overview



This document describes the on-premises network design supporting a cloud-first architecture for a 50–250 user organization.



The design focuses on:



- simplicity

- security

- segmentation

- controlled access to local resources



---



## 2. Network Components



Typical office infrastructure includes:



- Firewall / router

- Managed switches

- Corporate Wi-Fi

- Guest Wi-Fi

- Local servers

- Printers and scanners



---



## 3. VLAN Segmentation



The network is divided into logical segments:



### VLAN 10 – User Devices

- Workstations and laptops

- Entra ID joined devices

- Managed by Intune



### VLAN 20 – Servers

- Application server (payroll, accounting)

- File server or NAS (GIS, storage)

- Optional domain controller (if used)



### VLAN 30 – Printers / IoT

- Network printers

- Scanners

- Multi-function devices



### VLAN 40 – Guest Wi-Fi

- External users

- Internet-only access



### VLAN 50 – Management (optional)

- Network devices

- Admin access interfaces



---



## 4. Access Control Principles



### Default posture

- Deny by default

- Allow only required traffic



### Typical allowed flows



- Users → Internet → allowed

- Users → Servers → restricted to required ports

- IT/Admin → Servers → broader access

- Printers → Users → limited



### Blocked flows



- Guest → Internal network → blocked

- Printers → Servers → blocked (unless required)

- Lateral movement between segments → minimized



---



## 5. Firewall Strategy



The firewall enforces:



- VLAN isolation

- outbound internet access control

- inbound restrictions

- logging and monitoring



Recommended features:



- IDS/IPS

- application filtering

- geo-blocking (optional)

- VPN support (for remote users, not Azure)



---



## 6. Server Access Model



Access to local servers should be:



- restricted to authorized users or groups

- limited to required protocols (SMB, RDP, application ports)

 logged and monitored



Where possible:



- avoid exposing servers to the internet

- require internal network presence or controlled remote access



---



## 7. Printer and IoT Isolation



Printers and IoT devices are placed in a separate VLAN to:



- reduce attack surface

- prevent lateral movement

- isolate less secure devices



Access is typically:



- Users → Printers → allowed

- Printers → Users/Servers → restricted



---



## 8. Wi-Fi Design



Two main networks:



### Corporate Wi-Fi

- authenticated users

- access to internal resources

- mapped to user VLAN



### Guest Wi-Fi

- internet-only

- isolated from internal network

- separate VLAN



---



## 9. Internet Access Model



- All devices access cloud services directly over the internet

- No forced tunneling to Azure

- Microsoft 365, Entra ID and Intune are accessed securely using HTTPS



---



## 10. Remote Access Considerations



If remote access is required:



- VPN to office (not Azure)

- or Remote Desktop Gateway

- or application-specific remote access



Access should be:



- authenticated

- logged

- restricted



---



## 11. Backup and Resilience



- Local backups stored on NAS or backup server

- Optional offsite or cloud backup

- Regular testing of restore procedures



---



## 12. Monitoring



Recommended:



- firewall logs

- server logs

- endpoint security alerts

- basic network monitoring



---



## 13. Summary



This network design provides:



- strong segmentation

- controlled access

- compatibility with cloud-first services

- support for local workloads



It balances security, performance and simplicity, making it suitable for small and medium-sized organizations transitioning to modern cloud-based architectures.


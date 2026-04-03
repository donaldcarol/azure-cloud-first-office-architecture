# On-Premises Services



## 1. Overview



Although this architecture follows a cloud-first approach using Microsoft Entra ID, Intune and Microsoft 365, certain workloads are intentionally retained on-premises.



These services remain local due to:



- application compatibility constraints

- performance requirements

- large data volumes

- operational dependencies

- cost or licensing considerations



The goal is not to eliminate on-premises services entirely, but to keep only those that provide clear operational value.



---



## 2. Payroll and Accounting Systems



Payroll and accounting applications are typically retained on a local application server.



Reasons include:



- legacy application design

- dependency on local databases

- vendor limitations or lack of SaaS alternatives

- integration with local processes (printing, exports, reports)

- licensing constraints



### Access Model



- restricted to authorized users only

- accessible from the internal network

- optionally accessible via controlled remote access (VPN or RDP gateway)

- not exposed directly to the internet



---



## 3. GIS and Urbanism Workloads



The urbanism/GIS department works with large datasets, maps and CAD files.



These workloads are kept on local storage due to:



- large file sizes

- high read/write frequency

- sensitivity to latency

- limitations of cloud sync solutions for large engineering datasets



### Storage Model



- local file server or enterprise-grade NAS

- high-performance storage (SSD/NVMe recommended)

- structured shared folders (e.g. GIS, Urbanism, Projects)



---



## 4. Local File Storage



While most user and collaboration data is moved to OneDrive and SharePoint, local storage is used for:



- GIS/CAD data

- large archives

- technical datasets

- application-generated files



Cloud storage remains the primary platform for standard business documents.



---



## 5. Printing and Scanning



Printing and scanning services remain within the local office network.



### Printing



- network printers accessible via LAN

- optional integration with Universal Print

- deployment via Intune scripts or manual configuration



### Scanning



- scan to email (preferred)

- scan to network folder (where required)

- optional integration with SharePoint or cloud storage



---



## 6. Optional Local Directory (Minimal AD)



Although identity is managed in Microsoft Entra ID, a minimal on-premises Active Directory may be retained if required.



### Use Cases



- file shares with complex permissions (ACLs)

- legacy applications requiring domain membership

- Windows server management

- group-based access control for local resources



This AD instance is not the primary identity system, but a supporting component for legacy workloads.



---



## 7. Backup and Resilience



All on-premises services must be backed up regularly.



### Backup Scope



- application server (payroll/accounting)

- file server or NAS (GIS and storage)

- critical configuration data



### Strategy



- local backups (NAS or backup server)

- periodic offsite or cloud backup (optional)

- regular restore testing



---



## 8. Security Considerations



On-premises systems must follow strict security practices:



- servers placed in a dedicated VLAN

- restricted access from user networks

- no unnecessary internet exposure

- regular patching and updates

- endpoint protection enabled

- access logging and monitoring



Printers and IoT devices should be isolated in separate network segments.



---



## 9. Summary



On-premises services are retained only where necessary and justified.



This hybrid approach ensures:



- optimal performance for critical workloads

- compatibility with legacy applications

- reduced cloud complexity

- a balanced and pragmatic architecture



The long-term goal is continuous evaluation and gradual modernization where feasible.


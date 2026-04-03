# Azure Cloud-First Office Architecture



This repository presents a cloud-first architecture design for a 50–250 user organization using Microsoft Entra ID, Intune and Microsoft 365, while retaining selected on-premises services for line-of-business applications and GIS workloads.



The goal of this project is to demonstrate a realistic and pragmatic modern workplace architecture rather than a “cloud-only at any cost” approach. Identity, endpoint management, collaboration and security are cloud-based, while selected local services remain on-premises where performance, compatibility or operational constraints justify it.



---



## Scenario



Target organization profile:



- 1 main office

- 50–250 users

- Windows laptops and desktops

- Microsoft 365 for productivity and collaboration

- Cloud-based identity and endpoint management

- Local business applications for payroll and accounting
  
- Local GIS / urbanism workloads with large files

- No site-to-site VPN to Azure

- Focus on simplicity, security and operational realism



---



## Objectives



- Use \*\*Microsoft Entra ID\*\* as the primary identity platform

- Use \*\*Microsoft Intune\*\* for endpoint management

- Use \*\*Microsoft 365\*\* for collaboration and productivity

- Avoid unnecessary infrastructure in Azure when not required

- Retain selected on-premises services for legacy or performance-sensitive workloads

- Apply a modern security baseline with MFA, Conditional Access and device compliance

- Provide a scalable architecture suitable for a small or mid-sized organization



---



## High-Level Architecture



!\[High-Level Architecture](diagrams/high-level-architecture.png)



---



## Core Design Decisions



### 1. Cloud-first, not cloud-only

The architecture moves identity, endpoint management and productivity workloads to cloud services, but keeps selected local services on-premises when there is a valid technical or business reason.



### 2. No office-to-Azure VPN

A site-to-site VPN to Azure is intentionally excluded because the solution does not depend on private Azure-hosted workloads. Microsoft 365, Entra ID and Intune are consumed securely over the internet.



### 3. Entra ID joined devices

Workstations are designed to be \*\*Entra ID joined\*\* and managed through \*\*Intune\*\*, replacing traditional domain join + GPO approaches for endpoint management.



### 4. Local line-of-business applications remain on-premises

Payroll and accounting systems may remain on a local application server where software compatibility, licensing or operational requirements make cloud migration unnecessary or impractical.



### 5. GIS workloads stay local

Large GIS, CAD and urbanism files are assumed to be performance-sensitive and better suited to local storage over LAN rather than SharePoint or OneDrive synchronization.



---



## Solution Components



### Cloud Services

- Microsoft Entra ID

- Microsoft Intune

- Microsoft 365

&#x20; - Exchange Online

&#x20; - Teams

&#x20; - OneDrive

&#x20; - SharePoint Online



### Security Controls

- Multi-Factor Authentication (MFA)

- Conditional Access

- Device compliance policies

- BitLocker

- Microsoft Defender (where licensing permits)

- Administrative role separation



### On-Premises Components

- Office firewall/router

- Managed switches

- Corporate Wi-Fi

- Local application server

- Local file server or NAS for GIS/urbanism workloads

- Network printers / scanners

- Optional lightweight AD for legacy ACL/file share scenarios



---



## Network Design Summary



The office network is segmented into separate zones to reduce lateral movement and improve operational control.



Example VLAN layout:



- \*\*VLAN 10 – User Devices\*\*

- \*\*VLAN 20 – Servers\*\*

- \*\*VLAN 30 – Printers / IoT\*\*

- \*\*VLAN 40 – Guest Wi-Fi\*\*

- \*\*VLAN 50 – Management (optional)\*\*



See: \[Network Design](docs/network-design.md)



---



## Identity and Device Management



### Identity

Users are created in \*\*Microsoft Entra ID\*\* as cloud-managed identities.



### Devices

Endpoints are:

- Entra ID joined

- Enrolled into Intune

- Configured through compliance and configuration policies

- Provisioned through Autopilot where possible



### Typical Device Baseline

- BitLocker enabled

- Microsoft Defender enabled

- Firewall enabled

- Update rings configured

- Office apps deployed

- Teams deployed

- OneDrive configured



See: [Identity and Device Management](docs/identity-and-device-management.md)



---



## Security Baseline



This design assumes the following minimum controls:



- MFA for all users

- Conditional Access to require MFA

- Blocking of legacy authentication

- Compliant device requirement for sensitive applications

- Separate administrative accounts for privileged tasks

- Restricted access from guest networks to internal resources

- Network segmentation between users, servers and printers



See: [Security Baseline](docs/security-baseline.md)



---



## On-Premises Services



The following workloads are intentionally retained on-premises:



### Payroll and Accounting

- Local business application server

- Local database if required

- Restricted access from authorized users only



### GIS / Urbanism Data

- File server or NAS

- LAN-based access for better performance

- Suitable for large files and frequent edits

- Better aligned with engineering/GIS workflows than cloud sync



See: [On-Prem Services](docs/onprem-services.md)



---



## Why This Architecture Is Realistic



This project is designed around the practical reality that many organizations are not fully cloud-native. A modern architecture should not blindly move every workload to the cloud. Instead, it should modernize the areas that clearly benefit from cloud services while preserving local services where business continuity, software compatibility or performance require it.



This is especially relevant for:

- line-of-business applications

- accounting software

- payroll systems

- GIS/CAD-heavy departments

- organizations with one or more physical office locations



---



## Documentation



Detailed design notes are available in the `docs` folder:



- [Architecture Overview](docs/architecture-overview.md)

- [Network Design](docs/network-design.md)

- [Identity and Device Management](docs/identity-and-device-management.md)

- [Security Baseline](docs/security-baseline.md)

- [On-Prem Services](docs/onprem-services.md)

- [Migration Considerations](docs/migration-considerations.md)



---



## Sample Files



This repository also includes example supporting content:



- sample Intune-related PowerShell script

- onboarding notes

- design decision notes



See: \[samples](samples/)



---



## Future Enhancements



Possible future improvements include:



- Universal Print integration

- Defender for Endpoint integration

- phased hybrid identity model for legacy environments

- backup and archive strategy enhancements

- Azure-hosted DR options for selected workloads

- additional architectural diagrams



---



## Key Skills Demonstrated



- Cloud-first architecture design

- Microsoft Entra ID design thinking

- Intune endpoint management strategy

- Microsoft 365 integration

- Security baseline design

- Network segmentation

- Hybrid decision-making and trade-off analysis

- Pragmatic modernization planning



---



## Related Projects



You may also be interested in these related repositories:



- Azure Authentication Patterns

- Azure Terraform Foundation

- Azure VM Toolkit

- Azure Functions Lead Processing Demo



---



## Author



Created as a portfolio architecture project focused on modern workplace design, cloud identity, endpoint management and realistic hybrid decision-making for small and mid-sized organizations.


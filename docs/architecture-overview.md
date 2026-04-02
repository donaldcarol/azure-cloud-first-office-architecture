# Architecture Overview



## 1. Purpose



This document describes a cloud-first architecture designed for a small to medium-sized organization (50–250 users), combining Microsoft Entra ID, Intune and Microsoft 365 with selected on-premises services for business-critical workloads.



The goal is to modernize identity, endpoint management and collaboration while maintaining operational stability for legacy or performance-sensitive systems.



---



## 2. Business Context



The target organization has the following characteristics:



- Single primary office location

- 50–250 employees

- Windows-based endpoints

- Microsoft 365 for collaboration

- Business applications for payroll and accounting

- A GIS/urbanism department working with large files

- Limited need for Azure-hosted infrastructure

- Desire to reduce on-premises complexity without disrupting operations



---



## 3. Design Principles



### Cloud-first, not cloud-only

Cloud services are used where they provide clear benefits, while on-premises services are retained where necessary.



### Simplicity over complexity

Avoid unnecessary Azure infrastructure such as VPN gateways when not required.



### Identity as the security perimeter

Access control is based on identity, device compliance and Conditional Access rather than network location.



### Performance-aware design

Workloads with high I/O or large files (e.g. GIS) remain on local storage.



### Incremental modernization

The architecture supports gradual migration rather than a full “big bang” transformation.



---



## 4. High-Level Architecture



The solution is divided into two main areas:



### Cloud Layer

- Microsoft Entra ID (identity)

- Microsoft Intune (device management)

- Microsoft 365 (productivity and collaboration)

- Security controls (MFA, Conditional Access, compliance)



### On-Premises Layer

- Office network (LAN, Wi-Fi, firewall)

- Application server (payroll, accounting)

- File server or NAS (GIS, large datasets)

- Printers and scanners



---



## 5. Identity Model



- All users are created and managed in Microsoft Entra ID

- Authentication is cloud-based

- MFA is enforced for all users

- Conditional Access policies control access to applications

- Administrative roles are separated from standard user accounts



---



## 6. Device Management Model



All endpoints are:



- Entra ID joined

- Managed by Microsoft Intune  
- Configured using compliance policies and configuration profiles



Typical baseline includes:



- BitLocker encryption  
- Microsoft Defender enabled

- Firewall enabled

- Automatic updates

- Standard application set (Office, Teams, browser)



---



## 7. Application Strategy



### Cloud-based applications

- Exchange Online

- Microsoft Teams

- SharePoint Online

- OneDrive



### On-premises applications

- Payroll systems

- Accounting software

- Legacy line-of-business applications



These remain local due to compatibility, licensing or operational constraints.



---



## 8. Data Strategy



### Cloud storage

- OneDrive for personal files

- SharePoint for team collaboration



### Local storage

- File server or NAS for:

&#x20; - GIS data

&#x20; - CAD files

&#x20; - large datasets

&#x20; - high-performance workloads



---



## 9. Networking Approach



- No site-to-site VPN to Azure

- Cloud services accessed directly over the internet

- Office network segmented using VLANs

- Firewall enforces access control between segments



---



## 10. Security Model



Key controls include:



- Multi-Factor Authentication (MFA)

- Conditional Access

- Device compliance enforcement

- BitLocker encryption

- Endpoint protection (Defender)

- Network segmentation

- Restricted access to servers



---



## 11. Benefits of This Approach



- Reduced infrastructure complexity

- Improved security posture

- Modern device management

- Better remote access experience

- Optimized performance for local workloads

- Scalable and adaptable architecture



---



## 12. Limitations



- Some legacy applications remain on-premises

- GIS workloads are not cloud-native

- No full zero-infrastructure model

- Requires careful network design and segmentation



---



## 13. Future Evolution



Potential future steps include:



- Gradual migration of selected workloads to Azure

- Adoption of Universal Print

- Integration with advanced security services (Defender suite)

- Hybrid identity (if required for legacy scenarios)

- Cloud-based backup or DR solutions


\# Security Baseline



\## 1. Overview



This document defines the security baseline for a cloud-first architecture using Microsoft Entra ID, Intune and Microsoft 365, combined with selected on-premises services.



The goal is to implement a strong, practical security posture suitable for a 50–250 user organization without excessive complexity.



\---



\## 2. Security Principles



\- Identity is the primary security boundary

\- Assume breach mindset (Zero Trust principles)

\- Least privilege access

\- Device trust and compliance

\- Network segmentation

\- Minimize attack surface

\- Monitor and respond



\---



\## 3. Identity Security



\### Multi-Factor Authentication (MFA)

\- Required for all users

\- Enforced via Conditional Access

\- Prefer authenticator apps over SMS



\### Conditional Access Policies



Minimum recommended policies:



1\. Require MFA for all users

2\. Block legacy authentication

3\. Require compliant device for sensitive apps

4\. Apply stricter controls for admins

5\. Optional: restrict access by location



\---



\## 4. Privileged Access



\- Separate admin accounts from user accounts

\- No daily use of privileged accounts

\- Limit number of global admins

\- Use role-based access control (RBAC)

\- Consider Just-In-Time access (PIM) where available



\---



\## 5. Device Security (Intune)



\### Compliance Policies

Devices must meet:



\- BitLocker enabled

\- Firewall enabled

\- Antivirus enabled

\- OS version compliant

\- No jailbreak/root



\### Configuration Profiles

\- Disable insecure settings

\- Enforce password/PIN policies

\- Configure screen lock timeout

\- Restrict removable media (optional)



\---



\## 6. Endpoint Protection



\- Microsoft Defender enabled

\- Real-time protection active

\- Cloud protection enabled

\- Regular updates

\- Attack surface reduction rules (if applicable)



\---



\## 7. Data Protection



\### Cloud Data

\- OneDrive and SharePoint with versioning

\- Access controlled via Entra groups

\- Sharing restrictions configured



\### Local Data

\- Stored on file server or NAS

\- Access controlled via permissions

\- Regular backups



\---



\## 8. Network Security



\- VLAN segmentation (users, servers, printers, guest)

\- Firewall rules:

&#x20; - allow only required traffic

&#x20; - block unnecessary lateral movement

\- Guest network isolated

\- Printers and IoT isolated



\---



\## 9. Application Security



\- Prefer modern authentication (OAuth, SAML)

\- Avoid legacy protocols

\- Limit access to business applications

\- Monitor usage and access



\---



\## 10. Logging and Monitoring



Minimum monitoring includes:



\- Sign-in logs (Entra ID)

\- Audit logs

\- Endpoint alerts

\- Firewall logs



Optional enhancements:

\- Centralized logging

\- SIEM integration (e.g., Microsoft Sentinel)



\---



\## 11. Backup and Recovery



\- Regular backups for:

&#x20; - file server

&#x20; - application server

\- Test restore procedures

\- Optional cloud backup



\---



\## 12. Remote Access Security



\- Secure VPN (to office, if used)

\- MFA required

\- Restricted access

\- Logging enabled



\---



\## 13. Security Risks



Common risks:



\- weak passwords or MFA bypass

\- unmanaged devices

\- legacy authentication

\- flat networks

\- overprivileged users



\---



\## 14. Summary



This baseline provides:



\- strong identity protection

\- secure device posture

\- controlled network access

\- practical and scalable security



It is designed to balance security and usability for small and medium-sized organizations.


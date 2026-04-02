# Identity and Device Management



## 1. Overview



This document describes how identity and endpoint management are implemented using Microsoft Entra ID and Microsoft Intune.



The goal is to replace traditional Active Directory and Group Policy with a modern cloud-based approach.



---



## 2. Identity Platform



Microsoft Entra ID is used as the primary identity provider.



### Key characteristics:

- Cloud-managed identities

- Central authentication point

- Integration with Microsoft 365

- Supports Conditional Access and MFA



---



## 3. User Management



### User creation

- Users are created directly in Entra ID

- Naming convention: firstname.lastname@company.com



### Group structure



Groups are used for:



- application access

- device policies

- department segmentation



Examples:



- GRP-Sales

- GRP-HR

- GRP-IT

- APP-CRM-Users

- DEV-Standard-Users



---



## 4. Device Enrollment



All endpoints are:



- Entra ID joined

- Enrolled into Intune



### Enrollment methods:

- Windows Autopilot (preferred)

- Manual enrollment (fallback)



---



## 5. Device Provisioning (Autopilot)



Typical process:



1\. Device is delivered to user

2\. User signs in with Entra account

3\. Device joins Entra ID

4\. Intune enrollment is triggered

5\. Policies and applications are deployed automatically



This enables zero-touch provisioning.



---



## 6. Configuration Management



Intune replaces traditional GPO.



### Configuration includes:



- security settings

- device restrictions

- Wi-Fi and VPN profiles

- browser settings

- OS configurations



---



## 7. Compliance Policies



Devices must meet defined security requirements:



- encryption enabled

- antivirus active

- firewall enabled

- OS up to date



Non-compliant devices can be blocked via Conditional Access.



---



## 8. Application Deployment



Applications are deployed through Intune:



- Microsoft 365 Apps

- Teams

- browsers

- business applications

- Win32 packaged apps



---



## 9. Update Management



- Windows Update rings

- staged deployment

- automatic patching



---



## 10. Access Control



Access to applications is controlled by:



- user identity

- group membership

- device compliance

- Conditional Access policies



---



## 11. Onboarding Process



1\. Create user in Entra ID

2\. Assign groups

3\. Assign licenses

4\. Provide device (Autopilot)

5\. User logs in and receives configuration



---



## 12. Offboarding Process



1\. Disable account

2\. Revoke sessions

3\. Remove access

4\. Transfer data

5\. Wipe or retire device



---



## 13. Hybrid Considerations



If required:



- minimal on-prem AD may be retained

- used only for:

&#x20; - file shares

&#x20; - legacy applications

&#x20; - server management



However, user authentication remains cloud-based.



\---



## 14. Benefits



- simplified management

- centralized control

- improved security

- better remote support

- reduced infrastructure dependency



---



## 15. Challenges



- legacy application compatibility

- user training

- initial setup complexity

- dependency on cloud services



---



## 16. Summary



This model provides a modern identity and device management approach using Entra ID and Intune, replacing traditional AD/GPO while supporting both cloud and selected on-prem workloads.


# Entra ID Creation

## What this project is
A hands-on lab simulating identity creation and access management in Microsoft Entra ID, including group-based access and MFA configuration.

## What I did
- Created test users
- Configured groups (Admin, Power User, Read-Only)
- Set up MFA
- Configured a sign-in policy

## What I learned
Explanation due*

## MFA
I enabled MFA on my admin account because privileged accounts are the highest-risk identities in a tenant

<img width="974" height="700" alt="Screenshot 2026-07-22 at 14 26 47" src="https://github.com/user-attachments/assets/e88beb89-630a-4f13-930c-43e7e0e5fb40" />
<img width="974" height="443" alt="Screenshot 2026-07-22 at 14 29 23" src="https://github.com/user-attachments/assets/8b3dc0f6-fff7-44b6-9cba-c2bb66aca459" />
<img width="974" height="679" alt="Screenshot 2026-07-22 at 14 37 27" src="https://github.com/user-attachments/assets/bc984bae-09c5-4557-a255-e6195a163d4a" />

## New Test Users Creation

<img width="987" height="463" alt="Screenshot 2026-07-22 at 14 43 22" src="https://github.com/user-attachments/assets/ddb2ee91-d4a6-4135-bf63-90b8b82c8b75" />

In addition to my own user account, I have created 3 test users that will represent different levels of access to internal systems.

**External Contractor** - Requires limited access as a third-party and should be deemed as a potential risk, therefore will not receive long-term access.

**Finance Manager** - Internal user who will require privileged access to Finance related data & applications.

**New Hire User** - Least privilege access. Business unit application & data access with read permissions unless stated otherwise. 

## Group Creation

<img width="993" height="497" alt="Screenshot 2026-07-22 at 15 14 40" src="https://github.com/user-attachments/assets/f059a787-4a37-42cf-8065-4952de34a0a1" />

**All users** - 

**Contractors** - 

**Managers** - 

**Privileged Admins** - 

Explanation due*

## Security Defaults
<img width="953" height="243" alt="Screenshot 2026-08-21 at 11 40 13" src="https://github.com/user-attachments/assets/6d481cf5-95c0-48b5-a5b5-943432704054" />
Conditional Access was unavailable in this tenant because the required licensing was not present. I therefore reviewed Security defaults as the available baseline protection. Security defaults provide tenant-wide MFA and basic identity protections, but they do not provide the granular role-, location-, device-, or risk-based controls available with Conditional Access.

## Admin Role Assignments
<img width="963" height="373" alt="Screenshot 2026-08-21 at 11 47 09" src="https://github.com/user-attachments/assets/675f89d6-2fb0-426f-bb86-5426e3d1eeb0" />
I reviewed the Global Administrator assignment in my Entra ID lab. **_Only_** my designated admin account holds this highly privileged role. Sample users are not assigned Global Administrator permissions, which supports least privilege and reduces the impact of a compromised standard account.

## Reviewing lower privilege roles
<img width="963" height="373" alt="Screenshot 2026-08-21 at 11 53 14" src="https://github.com/user-attachments/assets/f6b0c394-269b-433d-b9fd-d4efca22794b" />
I reviewed the Helpdesk Administrator role as a lower-privilege alternative to Global Administrator. A helpdesk role can support tasks such as password resets for eligible non-administrator users, without granting unrestricted tenant-wide control. No users were assigned this role in my initial lab design therefore negating privilege creep for non-applicable users. 

## Privilege admins group
<img width="963" height="373" alt="Screenshot 2026-08-21 at 11 57 51" src="https://github.com/user-attachments/assets/a7dc619f-2c83-4e81-ab72-4d3eb7c17d1a" />
The Privileged Admins group contains only my designated administrator account as desired. I reviewed the membership to ensure that standard users, managers, and contractors do not have membership in a group intended for privileged identities.

## Audit Logs
<img width="1216" height="374" alt="Screenshot 2026-08-21 at 12 08 00" src="https://github.com/user-attachments/assets/c1d1adbc-c9cb-4d10-9755-2afc3efd3f0d" />
I reviewed Microsoft EntraID audit logs for the Privileged Admins group. I enable user '_Finance Manager_' a '_Privileged Admin_' (and immediately removed them) solely for demo purposes to ensure the logs record administrative changes such as group creation and membership updates. This provides accountability and supports investigations into identity changes & in the appropriate environments, allows logs to be sent to SIEMS for monitoring, alerting & investigation where necessary. 

## Sign-in attempts
<img width="807" height="282" alt="Screenshot 2026-08-21 at 12 17 26" src="https://github.com/user-attachments/assets/2adcfcb0-24ec-484a-a7c2-29119bdf4afc" />
<img width="891" height="523" alt="Screenshot 2026-08-21 at 12 17 00" src="https://github.com/user-attachments/assets/2d21281f-4aaa-4af8-8176-774288ffa395" />
I reviewed Microsoft Entra sign-in logs for my administrator account. The logs provide visibility into authentication attempts, including outcome, date and time, application, source IP address, and available authentication details. In a production environment, this information supports investigation of suspicious sign-ins and detection of abnormal access patterns. Please note, 'IP addresses' & 'Resource ID' have been removed for confidentiality. I also experimented with VPN enablement in Germany to showcase 'Location' variety. 


## RBAC Matrix
<img width="723" height="353" alt="Screenshot 2026-08-21 at 12 44 45" src="https://github.com/user-attachments/assets/c3dd8cec-124e-4162-8b95-b5253cc5e443" />
My lab uses a group-based access design: standard, manager, contractor, and privileged identities are separated into clearly named groups. Only my designated administrator account holds the Global Administrator role. I reviewed Helpdesk Administrator as a lower-privilege alternative but did not assign it, because there is no current support requirement in this small lab.

This Matrix would be either more established in a live environment or fluid in a growing environment where more business units and variables need to be considered. 

## JML Workflow

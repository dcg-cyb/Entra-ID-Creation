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
[View the JML workflow](docs/joiner-mover-leaver.md)

# Summary
## Microsoft Entra ID Security Lab

## Overview

This project documents my hands-on beginner Microsoft Entra ID lab. I built and documented a small identity environment to demonstrate core Identity and Access Management (IAM) principles, including MFA, Security defaults, least privilege, role-based access control, identity monitoring, audit logging, and joiner-mover-leaver processes.

## Lab Objectives

- Create and manage test users and security groups.
- Register MFA for a privileged administrator account.
- Review Microsoft Entra Security defaults as the baseline control available in my tenant.
- Apply least-privilege thinking to privileged roles and group membership.
- Review audit logs and sign-in logs for identity monitoring.
- Document an RBAC model and Joiner–Mover–Leaver workflow.
- Explain how Entra logs could be forwarded to a SIEM in a production environment.

## Lab Design

| Identity type | Example identity | Group | Administrative access |
|---|---|---|---|
| Privileged Administrator | Darius Goldsmith | Privileged Admins | Global Administrator |
| Standard User | New Hire User | All Users | No admin role |
| Manager | Department Manager | All Users, Managers | No admin role |
| Contractor | External Contractor | All Users, Contractors | No admin role |

## Security Controls Demonstrated

### MFA and Security Defaults

MFA was registered for my privileged administrator account. Security defaults were already enabled in the tenant, providing baseline identity protection including MFA requirements and legacy authentication protection.

### Least Privilege and RBAC

Only my designated administrator account holds the Global Administrator role. Standard users, managers, and contractors do not hold Entra administrative roles. I reviewed the Helpdesk Administrator role as a lower-privilege option for support tasks, but no account was assigned because my lab has no current support requirement.

- [View the RBAC matrix](docs/RBAC-Matrix.md)

### Monitoring and Auditability

I reviewed Microsoft Entra audit logs for privileged-group changes and sign-in logs for my administrator account. These logs provide evidence of identity changes and authentication activity. In a production environment, diagnostic settings could forward Entra audit and sign-in logs to a SIEM such as Microsoft Sentinel for centralised monitoring, alerting, investigation, and retention.

### Joiner–Mover–Leaver Governance

I documented a Joiner–Mover–Leaver process to show how user access should be created, reviewed during role changes, and removed during offboarding.

- [View the JML workflow](docs/joiner-mover-leaver.md)

## Licensing Limitation and Future Design

This tenant does not include the Microsoft Entra ID P1 licence required for Conditional Access. Instead, Security defaults provide the available baseline protection in this lab.

In a production design with Entra ID P1 or P2, I would create a Conditional Access policy to require MFA for privileged administrators, initially deploy it in Report-only mode, review the impact, and then enforce it. I would also investigate device, location, and sign-in-risk conditions based on the organisation’s requirements.

## Evidence

Evidence captured during this lab includes:

- User and group configuration screenshots.
- MFA registration evidence.
- Security defaults review.
- Global Administrator and Helpdesk Administrator role review.
- Privileged Admins group membership review.
- Microsoft Entra audit-log review.
- Administrator sign-in-log review.
- RBAC matrix and Joiner–Mover–Leaver documentation.

> Screenshots have been reviewed before publication to avoid exposing passwords, tenant IDs, IP addresses, or other sensitive information.

## Key Learning Outcomes

- Identity is a security perimeter: compromised credentials can lead directly to unauthorised access.
- MFA and Security defaults provide foundational protection for identity-based attacks.
- Least privilege reduces the impact of compromised accounts and administrative mistakes.
- Audit and sign-in logs support accountability, detection, and investigation.
- Identity governance requires ongoing lifecycle management, not just account creation.

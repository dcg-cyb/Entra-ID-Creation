# Entra ID Creation

## What this project is
A hands-on lab simulating identity creation and access management in Microsoft Entra ID, including group-based access and MFA configuration.

## What I did
- Created test users
- Configured groups (Admin, Power User, Read-Only)
- Set up MFA
- Configured a sign-in policy

## What I learned
...
## MFA
I enabled MFA on my admin account because privileged accounts are the highest-risk identities in a tenant

<img width="974" height="700" alt="Screenshot 2026-07-22 at 14 26 47" src="https://github.com/user-attachments/assets/e88beb89-630a-4f13-930c-43e7e0e5fb40" />
<img width="974" height="443" alt="Screenshot 2026-07-22 at 14 29 23" src="https://github.com/user-attachments/assets/8b3dc0f6-fff7-44b6-9cba-c2bb66aca459" />
<img width="974" height="679" alt="Screenshot 2026-07-22 at 14 37 27" src="https://github.com/user-attachments/assets/bc984bae-09c5-4557-a255-e6195a163d4a" />

## New Test Users

<img width="987" height="463" alt="Screenshot 2026-07-22 at 14 43 22" src="https://github.com/user-attachments/assets/ddb2ee91-d4a6-4135-bf63-90b8b82c8b75" />

In addition to my own user account, I have created 3 test users that will represent different levels of access to internal systems.

**External Contractor** - Requires limited access as a third-party and should be deemed as a potential risk, therefore will not receive long-term access.

**Finance Manager** - Internal user who will require privileged access to Finance related data & applications.

**New Hire User** - Least privilege access. Business unit application & data access with read permissions unless stated otherwise. 

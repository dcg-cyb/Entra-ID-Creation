# Conditional Access
As this is a home lab, I do not have sufficient access to create conditional access policies however here are a range of policies I would look to enforce. 

- If a user signs in from a remote location in which the organisation DOES NOT operate or have entities in, access should be blocked
- If a user leverage a legacy email client (over browser email use), access should be blocked
- WHEN a user within the 'Manager' group signs in, they MUST be using an Intune compliant device or company issued and registered device.
- WHEN a user signs in from an external network, they MUST leverage MFA to sign on in additional to account credentials

# Joiner–Mover–Leaver (JML) Workflow

## Purpose

This workflow describes how identities and access should be managed throughout a user's lifecycle in the Entra ID lab. It supports least privilege by ensuring access is granted, reviewed, changed, and removed when required.

## Joiner

1. Create the user account in Microsoft Entra ID.
2. Assign the user to the `All Users` group.
3. Add role-specific group membership where needed:
   - Managers join the `Managers` group.
   - Contractors join the `Contractors` group.
4. Require MFA registration through Security defaults.
5. Confirm the user has no unnecessary Entra administrative role.

## Mover

1. Review the user's existing groups and access.
2. Remove access linked to the previous role.
3. Add only the group membership needed for the new role.
4. Confirm the user does not retain unnecessary admin access.
5. Record the change in Microsoft Entra audit logs.

## Leaver

1. Block sign-in for the user account.
2. Revoke active sessions.
3. Remove the user from all groups.
4. Remove any Entra administrative role assignments.
5. Retain audit-log evidence of the offboarding action in line with organisational retention requirements.

## Security Rationale

The JML process reduces the risk of orphaned accounts, stale group membership, and excessive permissions. The mover stage is especially important because people can accumulate access across multiple job roles if previous permissions are not reviewed and removed.

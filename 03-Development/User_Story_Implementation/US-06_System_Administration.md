# US-06 – System Administration

## User story

**As a** System Administrator, **I want** to manage application configuration and access, **so that** the application can be maintained and users can perform authorized operations.

## Objective

Establish the administrative role and application access configuration needed to maintain the scoped application.

## ServiceNow components

- Five application roles.
- ACL rules for custom application tables.
- Application configuration and navigator modules.
- ServiceNow administrative capabilities.

## Configured application roles

- `hospital staff`
- `laboratory officer`
- `public health officer`
- `field investigation officer`
- `system administrator`

## Administrative access

The project implementation notes state that the System Administrator role has full CRUD access to the following custom tables through configured ACLs:

1. Disease Case
2. Hospital
3. Laboratory Report
4. Investigation
5. Outbreak Alert

## Implementation summary

1. Application roles were configured as part of application development.
2. ACL rules were created for the custom application tables.
3. The System Administrator role was configured for full CRUD access.
4. The application navigator includes Disease Cases, Laboratory Reports, Outbreak Alert, and Investigations modules.

## Verification

The project owner reports US-06 as completed and verified.

## Scope clarification

This story uses ServiceNow's administrative capabilities and configured application roles/ACLs. The project context does **not** establish that a separate custom user-management interface was built; this document does not claim one.

## Evidence

- Application roles and navigator modules: `../../../../ScreenShots/Phase-03/`
- ACL configuration and role impersonation tests: `../../../../ScreenShots/Phase-04/`

## Related stories

- US-03 – Public Health Officer Case Review
- US-04 – Field Investigation Management

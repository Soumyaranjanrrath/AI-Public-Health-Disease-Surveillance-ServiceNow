# US-06 – Administrator: User and System Management

## Jira reference

**Issue:** PHDS-8  
**Status shown:** Done

## User story

**As an** Administrator, **I want** to manage users, roles, hospitals, and disease information, **so that** the surveillance platform remains properly configured and controlled.

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

The Jira completion note states that the System Administrator role has full Create, Read, Write, and Delete permissions for the application's core tables:

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

The Jira completion note states that the System Administrator can access and manage the application's data and configuration.

**Jira status:** Done.

## Scope clarification

This evidence supports the System Administrator role and table-access configuration. It does not, by itself, establish that a separate custom user-management interface was developed. This document does not claim one.

## Evidence

- Jira issue screenshot: `../../ScreenShots/Phase-01/Jira_User_Stories/Jira_US-06_PHDS-8.png`
- Application roles, navigator modules, ACL configuration, and administrative access tests: add actual ServiceNow screenshots under `ScreenShots/Phase-03/` and `ScreenShots/Phase-04/`.

Two supplied Jira screenshots show the same issue PHDS-8. They are separate views of one Jira story, not separate user stories.

## Related stories

- US-03 – Public Health Officer Case Review
- US-04 – Field Investigation Management

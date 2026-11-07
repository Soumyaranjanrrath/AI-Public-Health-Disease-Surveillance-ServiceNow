# US-04 – Field Investigation Officer: Investigation Management

## Jira reference

**Issue:** PHDS-6  
**Status shown:** Done

## User story

**As a** Field Investigation Officer, **I want** to update investigation details for an assigned disease case, **so that** investigation findings can be recorded in the system.

## Objective

Provide a structured Investigation table and form for recording and maintaining field investigation work.

## ServiceNow components

- Investigation custom table.
- Investigation form.
- Field Investigation Officer application role.
- ACL configuration for investigation operations.

## Investigation information

The Jira completion note identifies these updateable details:
- Investigation Status.
- Findings.
- Contact Tracing Information.
- Other relevant investigation details.

## Access policy

The completion note states that the Field Investigation Officer can:
- Create Investigation records.
- View Investigation records.
- Update existing Investigation records.
- Not delete Investigation records.

## Implementation summary

1. The Investigation table and form were created.
2. The Field Investigation Officer role was configured.
3. ACLs were applied to control investigation record operations.
4. Role impersonation was used to test the configured permissions.

## Verification

The project notes record test investigation `INV0001003`. The project owner reports US-04 as completed and verified.

**Jira status:** Done.

## Evidence

- Jira issue screenshot: `../../../../ScreenShots/Phase-01/Jira_User_Stories/Jira_US-04_PHDS-6.png`
- Investigation table, form, test record, and create/read/update/delete checks: add actual ServiceNow screenshots under `ScreenShots/Phase-03/` and `ScreenShots/Phase-04/`.

## Notes

The exact internal field names and any assignment rules should be documented from the ServiceNow form and configuration screenshots.

## Related stories

- US-01 – Disease Case Reporting
- US-03 – Public Health Officer Case Review
- US-06 – System Administration
- US-12 – AI-Assisted Investigation Insights

# US-04 – Field Investigation Management

## User story

**As a** Field Investigation Officer, **I want** to create and maintain investigation records, **so that** field investigation activities can be tracked in the application.

## Objective

Provide a structured Investigation table and form for recording and maintaining field investigation work.

## ServiceNow components

- Investigation custom table.
- Investigation form.
- Field Investigation Officer application role.
- ACL configuration for investigation operations.

## Access policy

The documented configuration allows the Field Investigation Officer to:
- Create investigation records.
- Read investigation records available to the role.
- Update investigation records.
- Not delete investigation records.

## Implementation summary

1. The Investigation table and form were created.
2. The Field Investigation Officer role was configured.
3. ACLs were applied to control investigation record operations.
4. Role impersonation was used to test the configured permissions.

## Verification

The project notes record a test investigation:

- **Test record:** `INV0001003`

The project owner reports US-04 as completed and verified.

## Evidence

- Investigation table, form, and role configuration: `../../../../ScreenShots/Phase-03/`
- Test record and create/read/update/delete permission checks: `../../../../ScreenShots/Phase-04/`

## Notes

The exact investigation field list and any assignment rules should be documented from the ServiceNow form screenshots when available.

## Related stories

- US-01 – Disease Case Reporting
- US-03 – Public Health Officer Case Review
- US-06 – System Administration
- US-12 – AI-Assisted Investigation Insights (planned)

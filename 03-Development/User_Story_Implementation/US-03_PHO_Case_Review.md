# US-03 – Public Health Officer: Case Review

## Jira reference

**Issue:** PHDS-5  
**Status shown:** Done

## User story

**As a** Public Health Officer, **I want** to review reported and verified disease cases, **so that** I can decide what action is required for each case.

## Objective

Provide Public Health Officers with access to disease case information required for surveillance review while enforcing read-only access to case records.

## ServiceNow components

- Disease Case table and form.
- Public Health Officer application role.
- Table and field ACL configuration.

## Review information

The Jira completion note states that PHO can view:
- Disease details.
- Case status.
- Laboratory verification status.
- Severity.
- Date reported.
- Symptom onset date.
- Patient information.
- Location details.

## Access behavior

The Jira completion note explicitly states that the Public Health Officer has read-only access to case information and cannot modify the records.

## Implementation summary

1. The Public Health Officer role was configured.
2. ACL rules were used to control case access.
3. The role was impersonated to verify the intended read-only behavior.

## Verification

The project owner reports US-03 as completed and verified.

**Jira status:** Done.

Exact ACL names and individual test identifiers should be transcribed from the ServiceNow configuration or screenshots if those details are needed.

## Evidence

- Jira issue screenshot: `../../../../ScreenShots/Phase-01/Jira_User_Stories/Jira_US-03_PHDS-5.png`
- PHO role, case review, impersonation, and read-only verification: add actual ServiceNow screenshots under `ScreenShots/Phase-03/` and `ScreenShots/Phase-04/`.

## Privacy note

Mask patient names and all personal details in publicly shared evidence.

## Related stories

- US-01 – Disease Case Reporting
- US-02 – Laboratory Verification
- US-06 – System Administration

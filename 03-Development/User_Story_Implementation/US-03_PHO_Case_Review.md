# US-03 – Public Health Officer Case Review

## User story

**As a** Public Health Officer, **I want** to review disease case information, **so that** I can assess reported cases using the available surveillance details.

## Objective

Provide Public Health Officers with access to the disease case information required for surveillance review while following the configured read-only access policy.

## ServiceNow components

- Disease Case table and form.
- Public Health Officer application role.
- Table/field ACL configuration.

## Review information

The project context identifies the following case information as relevant to PHO review:

- Disease name and disease status.
- Case status and severity.
- Laboratory verification status.
- Reporting and symptom-onset dates.
- Patient and location information.

## Access design

The PHO role is intended to have read-only access to case records. The project's role-based access testing notes record that PHO access was tested through impersonation and ACL verification.

## Implementation summary

1. The Public Health Officer role was configured.
2. ACL rules were used to control case access.
3. The role was impersonated to verify the intended read-only behavior.

## Verification

The project owner reports US-03 as completed and verified. The exact ACL names and individual test-case identifiers should be transcribed from the instance screenshots or Jira record when those are uploaded.

## Evidence

- PHO role and case access configuration: `../../../../ScreenShots/Phase-03/`
- Impersonation and read-only verification: `../../../../ScreenShots/Phase-04/`

## Notes

Do not publish real patient information in screenshots. Mask names and other personal details.

## Related stories

- US-01 – Disease Case Reporting
- US-02 – Laboratory Verification
- US-06 – System Administration

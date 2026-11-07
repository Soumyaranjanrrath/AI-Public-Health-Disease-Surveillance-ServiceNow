# US-01 – Hospital Staff: Disease Case Reporting

## Jira reference

**Issue:** PHDS-1  
**Status shown:** Done

## User story

**As a** Hospital Staff member, **I want** to report a suspected or confirmed disease case, **so that** the case can be recorded for public health surveillance.

## Objective

Provide a Disease Case table and form for capturing suspected or confirmed disease reports submitted by hospital staff.

## ServiceNow components

- Scoped application.
- Disease Case custom table.
- Disease Case form and configured fields.
- Hospital/reporting-facility information.
- Hospital Staff application role and access configuration.

## Fields and information captured

The Jira completion note confirms configuration of required fields, case status, severity, patient information, reporting facility, and reference fields. The implementation context identifies these form fields:

- Disease Name
- Disease Status
- Case Status
- Severity
- Date Reported
- Date of Symptom Onset
- Patient Name
- Patient Gender
- Location
- Reporting Facility
- Symptoms
- Description

Exact internal dictionary names and field types should be confirmed from the ServiceNow dictionary or implementation screenshots.

## Implementation summary

1. The Disease Case table was created in the scoped application.
2. The form was configured to capture disease, case status, severity, patient information, reporting facility, and reference information.
3. Hospital/reporting-facility information was included in the reporting workflow.
4. The Hospital Staff role was configured for the reporting workflow.

## Verification

The Jira completion note states that a disease case record was successfully created and verified:

- **Test record:** `DSC0001014`

**Jira status:** Done.

## Evidence

- Jira issue screenshot: `../../../../ScreenShots/Phase-01/Jira_User_Stories/Jira_US-01_PHDS-1.png`
- Disease Case table/form and test record: add actual ServiceNow screenshots under `ScreenShots/Phase-03/` and `ScreenShots/Phase-04/`.

## Privacy note

Use synthetic patient data in public screenshots. Mask real names, identifiers, contact details, and other personal information before publishing.

## Related stories

- US-02 – Laboratory Verification
- US-03 – Public Health Officer Case Review
- US-05 – Outbreak Monitoring

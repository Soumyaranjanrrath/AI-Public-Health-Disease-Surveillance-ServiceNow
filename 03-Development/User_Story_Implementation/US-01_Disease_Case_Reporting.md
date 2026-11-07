# US-01 – Disease Case Reporting

## User story

**As a** Hospital Staff member, **I want** to register disease cases in the application, **so that** reported cases are stored centrally and can be reviewed by authorized public health personnel.

## Objective

Provide an application form and a Disease Case record structure for capturing disease reports submitted by hospital staff.

## ServiceNow components

- Scoped application.
- Disease Case custom table.
- Disease Case form and configured fields.
- Hospital/reporting-facility information.
- Application role and associated access configuration.

## Data captured

The Disease Case form described during implementation includes the following information:

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

Additional fields may exist in the instance; this list reflects the fields recorded in the project implementation context.

## Implementation summary

1. The Disease Case table was created in the scoped application.
2. The case form was configured to capture patient, disease, clinical, date, location, and reporting-facility information.
3. The Hospital/reporting-facility information is available to support case reporting.
4. The Hospital Staff role is used for the reporting workflow.

## Verification

The project notes record a test Disease Case record:

- **Test record:** `DSC0001014`

The project owner reports US-01 as completed and verified.

## Evidence

Add the actual screenshots captured during implementation and Jira verification to the paths below when available.

- ServiceNow Disease Case table and form: `../../../../ScreenShots/Phase-03/`
- Test record and Jira completion evidence: `../../../../ScreenShots/Phase-04/`

## Limitations / notes

Use synthetic patient data in public screenshots and example records. Remove or mask patient names and other personal information before publishing evidence.

## Related stories

- US-02 – Laboratory Verification
- US-03 – Public Health Officer Case Review
- US-05 – Outbreak Monitoring

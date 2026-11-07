# US-02 – Laboratory Verification

## User story

**As a** Laboratory Officer, **I want** to record laboratory reports linked to disease cases, **so that** test results and verification status are available in the surveillance workflow.

## Objective

Provide a structured way to capture laboratory test information and associate it with a disease case.

## ServiceNow components

- Laboratory Report custom table.
- Laboratory Report form.
- Reference/link to the related Disease Case.
- Laboratory Officer application role and access configuration.

## Data captured

The implementation notes identify these Laboratory Report fields:

- Test Name
- Test Date
- Result
- Verification Status
- Report Attachment
- Related Disease Case

## Implementation summary

1. The Laboratory Report table was created.
2. The form was configured for test details, results, verification, and attachment information.
3. A report can be associated with the relevant Disease Case.
4. The Laboratory Officer role supports the laboratory reporting workflow.

## Verification

The project notes record a test Laboratory Report linked to Disease Case `DSC0001014`, with a Positive result and Pending verification status at the time of the recorded test.

The project owner reports US-02 as completed and verified.

## Evidence

Add actual implementation and test screenshots when available:

- Laboratory Report form and table: `../../../../ScreenShots/Phase-03/`
- Linked report and Jira completion evidence: `../../../../ScreenShots/Phase-04/`

## Notes

The recorded test state is an example from the implementation history. Do not interpret it as the current state of the live record without checking the ServiceNow instance.

## Related stories

- US-01 – Disease Case Reporting
- US-03 – Public Health Officer Case Review

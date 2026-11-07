# US-02 – Laboratory Officer: Laboratory Verification

## Jira reference

**Issue:** PHDS-2  
**Status shown:** Done

## User story

**As a** Laboratory Officer, **I want** to review and update laboratory results for a disease case, **so that** the reported case can be verified.

## Objective

Provide a structured way to capture laboratory test information and associate it with a disease case.

## ServiceNow components

- Laboratory Report custom table.
- Laboratory Report form.
- Reference to the related Disease Case.
- Laboratory Officer application role and access configuration.

## Fields captured

The Jira completion note confirms a Laboratory Report table with:
- Disease Case reference.
- Test Name.
- Test Date.
- Result.
- Verification Status.
- Report Attachment.

## Implementation summary

1. The Laboratory Report table was created.
2. The form was configured for test details, results, verification, and attachment information.
3. A report can be associated with the relevant Disease Case.
4. The Laboratory Officer role supports the laboratory reporting workflow.

## Verification

The Jira completion note records a laboratory report linked to Disease Case `DSC0001014`, with:
- **Result:** Positive.
- **Verification Status:** Pending.

The project owner reports US-02 as completed and verified. The displayed Pending value is the status of the sample at the time captured; it does not mean the user story itself was pending.

**Jira status:** Done.

## Evidence

- Jira issue screenshot: `../../ScreenShots/Phase-01/Jira_User_Stories/Jira_US-02_PHDS-2.png`
- Laboratory Report form and linked test record: add actual ServiceNow screenshots under `ScreenShots/Phase-03/` and `ScreenShots/Phase-04/`.

## Notes

The recorded test state is an example from the implementation history. Check the ServiceNow record before describing its current state.

## Related stories

- US-01 – Disease Case Reporting
- US-03 – Public Health Officer Case Review

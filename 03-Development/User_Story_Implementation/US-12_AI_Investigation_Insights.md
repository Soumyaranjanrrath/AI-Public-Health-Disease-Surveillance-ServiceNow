# US-12 – Field Investigation Officer: AI-Assisted Investigation Insights

## Jira reference

**Issue:** PHDS-14  
**Status shown:** In Progress  
**Jira assignee shown:** ANAMU YASHWANT

## User story

**As a** Field Investigation Officer, **I want** the system to analyze investigation findings and provide useful insights, **so that** important patterns can be identified more efficiently.

## Current status

<badge color="info">In Progress – Not completed</badge>

This story is active in Jira but has not been reported as completed or verified.

## Completion criteria recorded in Jira

The Jira issue describes the required capability as follows:

- Analyze investigation information such as field findings, exposure history, and contact-tracing details.
- Generate a useful summary or identify potential patterns.
- Potential patterns include common exposures, locations, or contact clusters.
- Associate the generated insight with the relevant investigation or disease case.
- Verify the result using sample investigation records.

## Implementation design still to be completed

Before marking this story Done, document the actual:
- Investigation fields submitted for analysis.
- AI model or service selected.
- Prompt, rule, or analysis logic.
- ServiceNow integration and data flow.
- Insight display and record-association design.
- User review/correction process.
- Privacy and access controls.
- Test cases and observed outputs.

These components are not represented as implemented because the story remains In Progress.

## Verification plan

1. Prepare synthetic investigation records with field findings.
2. Include approved synthetic exposure-history and contact-tracing examples.
3. Generate a summary or pattern insight.
4. Verify that the insight is associated with the correct investigation or disease case.
5. Review the output for unsupported statements and omitted context.
6. Test role permissions and handling of missing data.
7. Save screenshots and test outcomes.

## Evidence

The supplied Jira screenshot shows PHDS-14 as In Progress. No Jira attachment filename was visible in the supplied issue view. See [Jira issue screenshot](../../ScreenShots/Phase-01/Jira_User_Stories/Jira_US-12_PHDS-14.png). Add implementation and test screenshots only after they exist.

## Responsible-use and privacy note

Investigation details may contain sensitive personal information. Do not send real investigation or patient data to an external AI service without an approved security and privacy design. Generated insights must be reviewed by authorized personnel.

## Related stories

- US-04 – Field Investigation Management
- US-06 – System Administration
- US-09 – Public Health Dashboard and Analytics
- US-11 – AI-Assisted Case Prioritization

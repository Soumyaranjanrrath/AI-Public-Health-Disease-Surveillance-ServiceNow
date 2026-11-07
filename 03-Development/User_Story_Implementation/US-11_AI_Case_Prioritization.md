# US-11 – AI-Assisted Case Prioritization

## Jira reference

**Issue:** PHDS-13  
**Status shown:** In Progress  
**Jira assignee shown:** Moningi Vinay Kumar

## User story

**As a** Public Health Officer, **I want** disease cases to be prioritized based on severity and outbreak risk, **so that** high-priority cases can be reviewed first.

## Current status

<badge color="info">In Progress – Not completed</badge>

This story is actively tracked in Jira but has not been reported as completed or verified.

## Completion criteria recorded in Jira

- Implement an AI-assisted case prioritization mechanism using disease case severity and outbreak risk information.
- Configure priority levels such as **Critical, High, Medium, and Normal**.
- Display the priority information with the relevant Disease Case.
- Verify that Public Health Officers can identify high-priority cases.
- Test prioritization using cases with different severity and risk conditions.

## Implementation design still to be completed

Before marking this story Done, document the actual:
- Input fields and source of outbreak-risk information.
- Priority mapping or model logic.
- ServiceNow table/field changes.
- Flow, Business Rule, API, or other implementation components.
- PHO interface and permission behavior.
- Test cases covering severity and risk combinations.

These implementation details are not assumed in this document because the story remains In Progress.

## Verification plan

1. Prepare synthetic cases covering different severity levels.
2. Supply or simulate the applicable outbreak-risk inputs.
3. Verify the assigned priority against the implemented mapping.
4. Confirm the priority is visible to PHO users.
5. Test missing or invalid inputs.
6. Record test results and screenshots.

## Evidence

The supplied Jira screenshot shows PHDS-13 as In Progress. No US-11 implementation attachment was visible in that screenshot. Add implementation and test screenshots only after they exist.

## Related stories

- US-01 – Disease Case Reporting
- US-09 – Public Health Dashboard and Analytics
- US-10 – AI-Based Outbreak Risk Prediction
- US-12 – AI-Assisted Investigation Insights

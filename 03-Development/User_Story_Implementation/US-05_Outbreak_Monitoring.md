# US-05 – Public Health Officer: Outbreak Monitoring

## Jira reference

**Issue:** PHDS-7  
**Status shown:** Done

## User story

**As a** Public Health Officer, **I want** to monitor disease cases by location and time, **so that** I can identify possible outbreak situations.

## Objective

Automate the initial threshold-based detection of possible outbreak clusters and create an Outbreak Alert when the configured matching case count reaches the threshold.

## ServiceNow components

- Disease Case table.
- Outbreak Alert table.
- Flow Designer flow: `Outbreak Alert Monitoring`.
- Lookup Records action.
- Conditional logic and Create Record action.

## Initial detection logic

The initial US-05 flow is recorded as:

1. Trigger when a Disease Case is created.
2. Look up Disease Case records matching the trigger Disease Name and Location.
3. Check whether the matching-record count reaches the configured threshold of 3.
4. Create an Outbreak Alert when the threshold condition is met.

**Scope distinction:** The original US-05 implementation was threshold-based. The seven-day reporting-date condition and existing-alert case-count synchronization are documented as the US-07 enhancement.

## Outbreak Alert information

The Jira completion note states that the automatically created alert includes:
- Disease Name.
- Location.
- Case Count.
- Detection Date.
- Threshold.
- Alert Status.
- Time Window.
- Description.

The configured threshold used in the recorded test was 3.

## Verification

The Jira completion note records a test using three Dengue cases reported from Bhubaneswar. The workflow automatically generated:

- **Outbreak Alert:** `OUA0001001`
- **Case Count:** 3
- **Threshold:** 3

The project owner reports US-05 as completed and verified.

**Jira status:** Done.

## Evidence

- Jira issue screenshot: `../../../../ScreenShots/Phase-01/Jira_User_Stories/Jira_US-05_PHDS-7.png`
- Flow configuration: add the actual ServiceNow screenshot under `ScreenShots/Phase-03/`.
- Three matching test cases and generated alert OUA0001001: add actual ServiceNow screenshots under `ScreenShots/Phase-04/`.

## Known behavior before US-07

The initial threshold-only flow could generate repeated alerts when later case-creation events again satisfied the threshold. The subsequent US-07 work adds a lookup for existing alerts and synchronizes the case count on a matching alert.

## Related stories

- US-01 – Disease Case Reporting
- US-07 – Time-Based Outbreak Detection
- US-08 – Outbreak Alert Notifications

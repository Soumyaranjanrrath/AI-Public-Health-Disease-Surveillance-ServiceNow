# US-08 – Outbreak Alert Notifications

## Jira reference

**Issue:** PHDS-10  
**Status shown:** Done

## User story

**As a** Public Health Officer, **I want** to receive a notification when a possible outbreak is detected, **so that** I can take timely action.

## Objective

Configure automated notification delivery to the Public Health Officers group when an Outbreak Alert record is inserted or updated.

## ServiceNow components

- Outbreak Alert table.
- ServiceNow notification configuration.
- Public Health Officers group as the configured recipient audience.
- Gmail SMTP configuration for outbound email delivery.

Exact notification record names, event names, and field-token expressions should be taken from the instance screenshots if those details are needed.

## Notification content recorded in Jira

The configured notification includes:

- Outbreak Alert Number.
- Disease Name.
- Affected Location.
- Case Count.
- Threshold.
- Alert Status.
- Detection Date.
- Description.

## Implementation and verification described in Jira

1. An automated Outbreak Alert Notification was configured in ServiceNow.
2. The notification was set to notify the Public Health Officers group when an Outbreak Alert record is inserted or updated.
3. Gmail SMTP was configured for outbound email delivery.
4. The notification was tested by updating a sample Outbreak Alert record.
5. The Jira completion note states that the notification was generated and delivered to the configured email recipient.

**Jira status:** Done.

## Evidence

- Jira completion evidence: `../../ScreenShots/Phase-01/Jira_User_Stories/Jira_US-08_PHDS-10.png`
- Notification and SMTP configuration screenshots: `../../ScreenShots/Phase-03/`
- Sample alert update and delivered-notification evidence: `../../ScreenShots/Phase-04/`

Replace the phase-folder references with exact screenshot filenames when the implementation evidence is uploaded.

## Security note

Do not publish SMTP passwords, app passwords, email credentials, personal recipient addresses, or other secrets in screenshots or configuration exports. Use secure credential storage in the target instance.

## Related stories

- US-05 – Outbreak Monitoring
- US-07 – Time-Based Outbreak Detection
- US-09 – Public Health Dashboard and Analytics

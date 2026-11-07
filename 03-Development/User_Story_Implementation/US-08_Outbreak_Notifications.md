# US-08 – Outbreak Alert Notifications

## User story

**As a** Public Health Officer, **I want** to receive notifications when an outbreak alert is generated, **so that** relevant alert information is communicated to the appropriate public health personnel.

## Objective

Notify the configured audience when the application creates an outbreak alert.

## ServiceNow components

The project includes configured ServiceNow outbreak alert notifications associated with the Outbreak Alert workflow. Exact notification record names, channels, recipients, and event configuration should be confirmed from the implementation screenshots before being listed.

## Notification information

The intended alert information includes:

- Disease name.
- Location.
- Case count.
- Configured threshold.
- Alert status.

The precise message template and field tokens should match the deployed notification configuration.

## Implementation summary

1. Outbreak alert creation is used as the notification trigger point.
2. A ServiceNow notification is configured for the relevant alert event/record condition.
3. The notification communicates the outbreak information to its configured public-health recipients.

The detailed recipient and trigger configuration will be added from the actual instance evidence.

## Verification

The project owner reports US-08 as completed and verified. Exact notification test timestamps, recipients, and delivery-channel evidence have not been supplied in the current documentation set.

## Evidence

Add actual screenshots of:
- Notification configuration.
- Trigger/event condition.
- Recipient configuration.
- Generated alert and notification preview or delivery evidence.

Suggested locations: `../../../../ScreenShots/Phase-03/` and `../../../../ScreenShots/Phase-04/`.

## Notes

Do not publish real email addresses, personal contact details, or private instance information in screenshots.

## Related stories

- US-05 – Outbreak Monitoring
- US-07 – Time-Based Outbreak Detection
- US-09 – Public Health Dashboard and Analytics

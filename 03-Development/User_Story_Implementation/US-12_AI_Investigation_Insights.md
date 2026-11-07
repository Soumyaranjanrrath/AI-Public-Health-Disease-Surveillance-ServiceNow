# US-12 – AI-Assisted Investigation Insights

## User story

**As a** Field Investigation Officer, **I want** the system to provide AI-assisted insights from investigation information, **so that** investigation findings can be reviewed and summarized more efficiently.

## Status

<badge>Planned – Not implemented</badge>

The project owner has confirmed that US-12 is pending. This document describes a future enhancement only and does not claim that an AI model, API, prompt, ServiceNow flow, or summary interface has been implemented.

## Proposed objective

Explore an AI-assisted capability that can summarize investigation records and highlight patterns in the information entered by Field Investigation Officers.

## Proposed scope for design

Before development, define:

- Which Investigation fields are eligible for analysis.
- Whether exposure, contact, location, date, symptom, or other information is included.
- Whether the feature generates a concise summary, potential patterns, suggested follow-up questions, or a combination.
- Which model or service will perform the analysis.
- How sensitive investigation information will be protected.
- How outputs will be reviewed, corrected, and stored.
- Which roles may view or request insights.

The exact investigation data fields and output format must be confirmed from the application and agreed user story before implementation.

## Potential ServiceNow components

These are possible design elements, not completed components:

- An action or UI control for requesting an insight.
- A Flow Designer flow or server-side integration.
- A secured external AI endpoint, if selected.
- A result field or related insight record.
- A PHO/FIO review mechanism and audit trail.

## Acceptance criteria to define

1. Only authorized users can request or view investigation insights.
2. The service uses only the approved investigation information.
3. The output is clearly marked as AI-generated.
4. The user can review and correct the output before treating it as a case record or report.
5. The application handles empty, invalid, or excessively long source content.
6. The feature avoids exposing personal or sensitive information to an unapproved external service.
7. Test cases cover incomplete data, contradictory findings, and unsupported conclusions.

## Testing plan (future)

- Test a complete synthetic investigation record.
- Test records with missing fields.
- Test conflicting or ambiguous findings.
- Verify authorization for requesting and viewing insights.
- Verify that outputs are stored or displayed as designed.
- Verify that no sensitive data is sent outside the approved environment.

## Evidence

No US-12 implementation screenshots or test results are available because this story has not been implemented. Add Jira planning evidence now and implementation/test evidence after development.

## Responsible-use note

AI-generated summaries may omit context or produce unsupported statements. Investigation insights must remain advisory and require review by authorized personnel. Do not send real patient or investigation data to an external model without an approved privacy and security design.

## Dependencies

- Investigation records and workflow from US-04.
- Role and access configuration from US-06.
- Potential dashboard presentation through US-09.

## Related stories

- US-04 – Field Investigation Management
- US-06 – System Administration
- US-09 – Public Health Dashboard and Analytics
- US-11 – AI-Assisted Case Prioritization

# Jira Tracking and Evidence

## 1. Purpose

This page records the Jira issue keys, status shown in the supplied screenshots, completion notes, and attachment filenames visible in those screenshots for the Public Health Disease Surveillance project.

Jira issue status is a project-tracking signal. It is not, by itself, independent proof of every technical behavior. ServiceNow screenshots and test outputs should be linked from the implementation and testing documents as they are added.

## 2. Issue inventory

| User story | Jira issue | Status shown in screenshot | Notes |
|---|---|---|---|
| US-01 – Hospital Staff: Disease Case Reporting | PHDS-1 | Done | Disease Case table/form, required fields, test record DSC0001014. |
| US-02 – Laboratory Officer: Laboratory Verification | PHDS-2 | Done | Laboratory Report table, Disease Case reference, Positive result, Pending verification. |
| US-03 – Public Health Officer: Case Review | PHDS-5 | Done | PHO can review relevant case information; read-only access. |
| US-04 – Field Investigation Officer: Investigation Management | PHDS-6 | Done | FIO can create/view/update investigation details, but cannot delete. |
| US-05 – Public Health Officer: Outbreak Monitoring | PHDS-7 | Done | Disease/location matching; threshold 3; test alert OUA0001001. |
| US-06 – Administrator: User and System Management | PHDS-8 | Done | System Administrator full CRUD access to five core custom tables. |
| US-07 – Public Health Officer: Time-Based Outbreak Detection | PHDS-9 | Done | Seven-day time-window detection and updating case count on existing alerts. |
| US-08 – Public Health Officer: Outbreak Alert Notification | PHDS-10 | Done | Notification to PHO group on alert insert/update; Gmail SMTP delivery tested. |
| US-09 – Public Health Officer: Public Health Dashboard and Analytics | PHDS-11 | Done | Dashboard summary and analytical visualizations in ServiceNow Platform Analytics. |
| US-10 – AI-Based Outbreak Risk Prediction | Not visible in supplied screenshot batch | Not shown | Project owner reports completed and verified; API source and local test result supplied separately. |
| US-11 – Public Health Officer: AI-Assisted Case Prioritization | PHDS-13 | In Progress | Priority based on case severity and outbreak risk; priority levels specified. |
| US-12 – Field Investigation Officer: AI-Assisted Investigation Insights | PHDS-14 | In Progress | Analyze findings, exposure history, and contact tracing; generate summaries/pattern insights. |

## 3. Screenshot inventory

The supplied Jira screenshots are organized by the issue they show. The original Jira attachment filenames visible in the issue pages are reproduced here as displayed.

| Screenshot subject | Jira issue | Attachment filenames visible in Jira |
|---|---|---|
| US-01 – Disease Case Reporting | PHDS-1 | `image-20260831-150651.png`; `image-20260831-150614.png` |
| US-02 – Laboratory Verification | PHDS-2 | `image2.jpeg`; `image1.jpeg` |
| US-03 – PHO Case Review | PHDS-5 | `image-20260902-050631.png`; `WhatsApp Image 2026-08-31 at 10.41.05 PM.jpeg`; `WhatsApp Image 2026-08-31 at 10.40.48 PM.jpeg` |
| US-04 – Investigation Management | PHDS-6 | `image3.jpeg`; `image4.jpeg` |
| US-05 – Outbreak Monitoring | PHDS-7 | `Now11.jpeg`; `Nowwww.jpeg` |
| US-06 – User and System Management | PHDS-8 | `image-20260902-045050.png`; `Screenshot 2026-09-02 101318.png` |
| US-07 – Time-Based Outbreak Detection | PHDS-9 | `image-20261003-044428.png` |
| US-08 – Outbreak Alert Notification | PHDS-10 | `Screenshot 2026-10-03 235152.png`; `Screenshot 2026-10-03 235126.png` |
| US-09 – Dashboard and Analytics | PHDS-11 | `US-09.jpeg` |
| US-11 – AI-Assisted Case Prioritization | PHDS-13 | No Jira attachment filename visible in the supplied screenshot. |
| US-12 – AI-Assisted Investigation Insights | PHDS-14 | No Jira attachment filename visible in the supplied screenshot. |

Two supplied screenshots show the US-06 / PHDS-8 Jira issue. They are two views of the same issue, not two different user stories. The supplied batch contains no Jira issue screenshot for US-10.

## 4. Important completion details visible in Jira

### US-07 – PHDS-9

The completion note states that the workflow:
- Detects outbreak clusters using a seven-day time window.
- Uses Disease Name, Location, and case-count threshold.
- Creates an alert when the threshold is reached.
- Synchronizes the Case Count of an existing alert when new cases are submitted.
- Was tested for threshold and time-window conditions.

The story implementation document should therefore describe both branches: create a new alert when no matching alert exists, and update the case count of an existing matching alert.

### US-08 – PHDS-10

The completion note states that:
- A ServiceNow Outbreak Alert notification is configured.
- It notifies the Public Health Officers group when an Outbreak Alert record is inserted or updated.
- It includes alert number, disease name, affected location, case count, threshold, alert status, detection date, and description.
- Gmail SMTP was configured for outbound email.
- A sample Outbreak Alert update was used to test notification generation and delivery to the configured recipient.

### US-09 – PHDS-11

The completion note identifies:
- Summary visualizations for total disease cases, verified cases, active investigations, and possible outbreak alerts.
- Analytical visualizations by disease, location, severity, case status, investigation status, and outbreak alert status.
- ServiceNow Platform Analytics as the dashboard platform.

### US-11 – PHDS-13

The Jira issue is In Progress. Its completion criteria call for:
- Prioritization based on disease case severity and outbreak risk.
- Priority levels: Critical, High, Medium, and Normal.
- Displaying priority information with the relevant Disease Case.
- PHO visibility of high-priority cases.
- Testing with different severity and risk conditions.

### US-12 – PHDS-14

The Jira issue is In Progress. Its completion criteria call for:
- Analysis of field findings, exposure history, and contact-tracing details.
- A useful summary or pattern identification, such as common exposures, locations, or contact clusters.
- Association of the generated insight with the related investigation or disease case.
- Verification using sample investigation records.

## 5. US-10 tracking gap

US-10 is reported by the project owner as completed and verified. The supplied code and local test result support the existence of the FastAPI prediction prototype and a successful sample response. However, a Jira screenshot, Jira issue key, and screenshot of the complete ServiceNow-to-API execution were not included in this Jira screenshot batch.

Do not invent a Jira issue key or claim that the screenshot evidence was supplied.

## 6. Evidence publication checklist

- [ ] Add the supplied Jira issue screenshots to `ScreenShots/Phase-01/Jira_User_Stories/`.
- [ ] Link each image from this document using its repository filename.
- [ ] Add ServiceNow implementation screenshots under `ScreenShots/Phase-03/`.
- [ ] Add test execution screenshots under `ScreenShots/Phase-04/`.
- [ ] Add a Jira screenshot for US-10 if available.
- [ ] Keep US-11 and US-12 status as In Progress until implementation and verification are actually complete.

# Actors and Application Roles

## 1. Purpose

This document identifies the actors who interact with the AI-Enabled Public Health Disease Surveillance and Outbreak Response Platform and describes their responsibilities within the ServiceNow application.

The project includes five application roles.

## 2. Actor overview

| Actor / application role | Main responsibility |
|---|---|
| Hospital Staff | Submit disease case reports. |
| Laboratory Officer | Record and verify laboratory reports. |
| Public Health Officer (PHO) | Review cases, monitor outbreak alerts, and use dashboards and analytics. |
| Field Investigation Officer (FIO) | Create and maintain field investigation records. |
| System Administrator | Maintain application configuration, roles, and access. |

## 3. Role descriptions

### 3.1 Hospital Staff

**Purpose:** Provide disease case information to the surveillance application.

**Primary activities:**
- Create disease case records.
- Enter configured patient and disease details.
- Provide severity, case status, symptom onset, reporting date, location, and reporting facility information.

**Related user story:** US-01 – Disease Case Reporting.

### 3.2 Laboratory Officer

**Purpose:** Record laboratory information associated with reported disease cases.

**Primary activities:**
- Create laboratory report records.
- Associate a report with the relevant Disease Case.
- Enter test name, test date, result, verification status, and report attachment information as configured.

**Related user story:** US-02 – Laboratory Verification.

### 3.3 Public Health Officer (PHO)

**Purpose:** Review surveillance information and monitor possible outbreaks.

**Primary activities:**
- Review disease case information.
- Monitor outbreak alerts.
- Receive configured outbreak notifications.
- Use the public health dashboard and analytics.
- Access the US-10 outbreak risk prediction capability as implemented.

**Access note:** The project configuration intends PHO case access to be read-only. Actual table and field permissions are enforced by ServiceNow roles and ACLs.

**Related user stories:** US-03, US-05, US-07, US-08, US-09, US-10. In Progress: US-11.

### 3.4 Field Investigation Officer (FIO)

**Purpose:** Maintain field investigation information associated with surveillance activities.

**Primary activities:**
- Create investigation records.
- View assigned or accessible investigation information.
- Update investigation records according to configured permissions.
- Record investigation findings and related details supported by the application.

**Access note:** The configured role allows investigation record creation, reading, and updating while preventing deletion, as described in the project implementation notes.

**Related user story:** US-04 – Field Investigation Management. In Progress: US-12.

### 3.5 System Administrator

**Purpose:** Maintain the ServiceNow application and its access configuration.

**Primary activities:**
- Manage the configured application roles.
- Maintain access control configuration.
- Administer the custom application tables and application setup.
- Support application maintenance and configuration.

**Access note:** The project configuration provides the System Administrator role with full CRUD access to the custom application tables through configured ACLs.

**Related user story:** US-06 – System Administration.

## 4. ServiceNow application roles

The project defines the following application roles:

| Role name | Intended user |
|---|---|
| `hospital staff` | Hospital Staff |
| `laboratory officer` | Laboratory Officer |
| `public health officer` | Public Health Officer |
| `field investigation officer` | Field Investigation Officer |
| `system administrator` | System Administrator |

These are application role names recorded in the project implementation context. Instance-specific role identifiers and exact ACL names should be documented only after inspecting the ServiceNow configuration.

## 5. Access-control summary

| Role | Disease Case | Laboratory Report | Investigation | Administrative configuration |
|---|---|---|---|---|
| Hospital Staff | Case reporting access | Not specified here | Not specified here | No |
| Laboratory Officer | Case-linked workflow access | Laboratory reporting and verification | Not specified here | No |
| Public Health Officer | Read-only review policy | Review access as configured | Review access as configured | No |
| Field Investigation Officer | Access as configured | Access as configured | Create, read, update; no delete | No |
| System Administrator | Full CRUD | Full CRUD | Full CRUD | Yes |

**Important:** This table is a high-level summary of the project's described access policies, not a substitute for the actual ServiceNow ACL configuration. Where a permission is marked "not specified here" or "as configured," the exact operation should be verified against the instance before making a more specific claim.

## 6. Related application tables

The ServiceNow application includes the following five custom tables:

1. Disease Case
2. Hospital
3. Laboratory Report
4. Investigation
5. Outbreak Alert

No separate Disease Category table is assumed in this documentation.

## 7. Related documentation

- [Business Requirements Document](Business_Requirements_Document.md)
- [Functional Requirements](Functional_Requirements.md)
- [Project User Stories](User_Stories.md)
- [Solution Design](../02-Solution-Design/Solution_Design.md)

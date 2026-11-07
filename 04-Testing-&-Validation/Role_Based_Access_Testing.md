# Role-Based Access Testing

## 1. Purpose

This document records the role-based access policies and verification activities described for the ServiceNow application.

## 2. Configured roles

- `hospital staff`
- `laboratory officer`
- `public health officer`
- `field investigation officer`
- `system administrator`

## 3. Documented access policies

| Role | Documented access behavior |
|---|---|
| Hospital Staff | Disease case reporting workflow. Exact table-level operations should be confirmed from ACL evidence. |
| Laboratory Officer | Laboratory report creation and verification workflow. Exact table-level operations should be confirmed from ACL evidence. |
| Public Health Officer | Read-only access to Disease Case records for case review. |
| Field Investigation Officer | Create, read, and update Investigation records; delete is restricted. |
| System Administrator | Full CRUD access to the five custom application tables through configured ACLs. |

## 4. Custom tables in scope

1. Disease Case
2. Hospital
3. Laboratory Report
4. Investigation
5. Outbreak Alert

## 5. Verification approach

The implementation notes record that role impersonation was used to verify ACL behavior. Three read ACLs were specifically mentioned in the project history.

### Public Health Officer

1. Impersonate a user with the PHO role.
2. Open a Disease Case record.
3. Verify that case details can be read.
4. Attempt an update through the normal UI.
5. Confirm the configured read-only restriction prevents unauthorized modification.

### Field Investigation Officer

1. Impersonate a user with the FIO role.
2. Open an Investigation record.
3. Verify permitted create, read, and update operations.
4. Attempt deletion.
5. Confirm deletion is denied.

### System Administrator

1. Impersonate or use the System Administrator role.
2. Verify CRUD operations against the custom application tables.
3. Confirm access is consistent with the configured administrative ACLs.

## 6. Evidence status

The project owner reports the access-control story and role tests as completed and verified. Add the actual screenshots showing role impersonation, ACL records, and successful/denied operations under `ScreenShots/Phase-04/`.

Record exact ACL names, table names, operation results, and test user details only from the screenshots or ServiceNow configuration.

## 7. Security notes

- Do not publish credentials or session information.
- Mask usernames and personal details where necessary.
- Avoid including private instance URLs or authentication tokens in screenshots.
- Re-test access after any role or ACL changes.

## 8. Related documents

- [US-03 – PHO Case Review](../03-Development/User_Story_Implementation/US-03_PHO_Case_Review.md)
- [US-04 – Field Investigation](../03-Development/User_Story_Implementation/US-04_Field_Investigation.md)
- [US-06 – System Administration](../03-Development/User_Story_Implementation/US-06_System_Administration.md)

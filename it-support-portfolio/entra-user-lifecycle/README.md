# Entra / Microsoft 365 user lifecycle — LAB, COMPLETED Oct 26, 2026

Personal lab / demo — no production users, no paying clients, synthetic data only.
Tenant IDs, domains, and passwords are intentionally omitted from this write-up.

## What was done

Worked in a Microsoft Entra ID Free tenant, using the fictional Northline HVAC
company from `fake-company-note.md` (12 synthetic staff in 3 groups).

### Groups created (Security groups, Assigned membership)
- Office — billing + schedules, no payroll
- Technicians — job sheets only
- Dispatch — assign jobs + schedules, no payroll

Access is given by group (role), not person by person. That is the core idea:
change the group and the access changes, without recreating the account.

### Joiner — Maya Chen (synthetic user)
- Created a new cloud user account with a unique company login and an
  auto-generated temporary password, account enabled.
- Added Maya to the Office group.
- Verified: Office members listed Maya; total users went from 1 (owner) to 2.

Maps to: "create, update, and deactivate accounts, reset passwords, and
support MFA" and "user account administration, password support, and access
management" in Tier 1 / MSP postings.

### Mover — Maya moves Office to Dispatch
- Removed Maya from Office, added her to Dispatch.
- Verified: Office no longer listed Maya; Dispatch did.
- Lesson: a mover keeps the same login and history; only group membership
  changes, so billing access is lost and dispatch access is gained.

### Password reset
- Reset Maya's password to a new auto-generated temporary password, with
  change required on next sign-in.
- Lesson: a reset gives a temporary password only — the old password stops
  working, and the user sets their own on next login. Never reuse one
  password for everyone.
- MFA re-register procedure documented: if a user loses their phone,
  require them to re-register MFA (like issuing a new key fob). This step
  is only applicable if the user had MFA enrolled.

### Leaver — Maya leaves
- Blocked sign-in (account enabled off) — the same-day cut-off step.
- Removed Maya from Dispatch.
- Verified: Maya showed as blocked/disabled, and Dispatch no longer listed her.
- Account left disabled, not deleted, to preserve the record for audit —
  the realistic retention step, not an immediate delete.

## What this does NOT prove
- No Microsoft 365 licences, mailbox administration, or paid Entra features
  (no Conditional Access, no Lifecycle Workflows — those are not in Entra ID Free).
- No production on-call experience, no real users, no paid services used.
- The Microsoft 365 E5 developer sandbox route was not used: it is restricted
  to Visual Studio Pro/Enterprise subscribers and certain partner members.

## Free-tier note
The tenant shown in the portal was already on Microsoft Entra ID Free, so
user/group work in this lab did not require a paid Azure subscription or
paid services. Rules kept for this lab: user/group work only, never upgrade
to pay-as-you-go, never spin up paid services.

See `fake-company-note.md` for the full fictional company, groups, and
12 synthetic users.

# Entra user lifecycle — done Oct 26, 2026

This is a lab. No real users, no real company, no paid services. All the data is fake.

I used Microsoft Entra ID Free. I did not need any paid features for this.

## The fake company
Northline HVAC. 12 fake people, 3 groups. I made the groups as Security groups, and I added people manually.

- Office: billing and schedules, no payroll
- Technicians: job sheets only
- Dispatch: assign jobs and schedules, no payroll

I did it this way on purpose. If you give access by group, you do not have to set it person by person. Change the group, change the access.

## Joiner
I created Maya Chen, a fake user. I gave her a company login and a temp password, and I turned her account on.

Then I put her in Office. After that, Office listed her as a member. At that point there were 2 users in total: me and Maya.

## Mover
Then I moved Maya from Office to Dispatch. I took her out of Office and added her to Dispatch.

Her login stayed the same. Only her group changed. That means she lost billing access and gained dispatch access. That is the whole point of a mover. You do not delete her and start over.

## Password reset
I reset Maya's password to a new temp one, and set it so she would have to change it on next sign-in.

That is what a password reset actually is. The old password stops working, and the user sets their own new one. You do not reuse the same password for everyone.

I also wrote down the MFA reset step: if someone loses their phone, you make them set up MFA again from scratch. That only applies if they had MFA set up in the first place.

## Leaver
When Maya "left", I blocked her sign-in first. That is the same-day step. You do not wait to cut access.

Then I took her out of Dispatch. After that, Dispatch did not list her anymore, and her account showed as blocked.

I left her account blocked, not deleted. That way there is still a record.

## What I did not do
No Microsoft 365 licences. No mailbox admin. No Conditional Access or Lifecycle Workflows. Those are not in Entra ID Free, and I did not pretend I used them.

No paid Azure services. No pay-as-you-go upgrade.

The full fake company list is in fake-company-note.md. I left out tenant IDs, domains, and passwords on purpose.

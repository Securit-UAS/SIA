# TALOS Master Dashboard — r15

This build combines the Master Compliance dashboard and Incident Dashboard in one GitHub Pages package.

## Navigation
- `index.html` — Master Compliance
- `incident.html` — Incident Dashboard
- Top-bar buttons switch between Compliance and Incidents.
- Both pages use the same TALOS authentication storage key, so an authenticated user can switch views without a second login (subject to normal session validation).

## C247 profile link
The officer compliance card now includes **Open C247 Profile**.

Before opening C247, TALOS displays an information prompt explaining:
- C247 changes will not appear in TALOS until the scheduled reconciliation at approximately 05:30.
- Training and screening/declaration changes appear on the next dashboard refresh.

The C247 profile URL is generated from the officer Staff ID:
`https://c247.space/v1/staff_records.aspx?id={StaffID}`

## Existing behaviour retained
All r14 compliance logic is retained, including provider-name normalisation, module toggles, name matching, priority sorting and SIA licence-not-found treatment.

The supplied Incident Dashboard is retained as its own view and continues to use its existing incident API.

## r16 changes
- Exact canonical full-name equality now returns green before fuzzy/name-field logic.
- Same SIA licence across multiple C247 Staff IDs is a highest-priority critical issue.
- If a duplicate licence also returns a materially different SIA name, status is `Licence identity conflict`.
- Identity conflicts sort above `Licence not found` and use a stronger pulsing red row plus officer-card warning.

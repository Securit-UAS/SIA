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

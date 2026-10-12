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


## r17
Duplicate SIA licence logic refined: matching name + phone across different providers is an amber review; same-provider duplicates, identity mismatch or phone mismatch remain critical red.


## r18
- Made middle-name matching directional.
- SIA may contain additional middle-name detail without creating a mismatch when the C247 identity is otherwise an exact ordered match.
- C247-only additional middle-name detail is now a yellow Name review because it is not confirmed by the SIA return.
- Minor spelling differences alongside extra SIA middle-name detail remain yellow rather than silently passing.
- Existing exact-name, nickname, duplicate-licence and identity-conflict rules are retained.


## r19 changes
- Risk sorting now uses only enabled compliance modules. SIA-specific priorities and pulsing borders disappear when SIA is disabled.
- Added Sort rows control: Risk priority, Officer A-Z, Provider A-Z, Site A-Z, Manager A-Z.
- KPI totals now recalculate for selected Site and Company / Provider.
- Module-specific KPI cards are hidden when their module is disabled.
- The SIA 8-30 days status filter is hidden when SIA is disabled.

## r22 changes
- Simplified Compliance header: removed live-load status copy and descriptive subtitle text.
- Centred navigation buttons in the header; user identity and Sign out sit on the far right.
- Added Wall view navigation.
- Added `wallboard.html`: privacy-safe summary view, hourly data refresh, 60-second rotation through All companies, SecurIT and each labour provider, with pause/resume.


## r22 wallboard
- Wallboard rotation interval reduced to 30 seconds.
- Provider selector can pause the wallboard on a chosen company; Auto rotate resumes rotation.
- Expanded SIA, Training and Declaration module detail.
- Added Top Issues and lowest-compliance ranking panels; ranking switches to sites when viewing a provider.
- Added overall green/amber/red distribution strip.


## r22
Adds Appraisal / Site Visit compliance to the master dashboard, including latest-visit scoring, due dates, officer-card detail, status dots, filtered row shading, and appraisal-aware KPI/sorting logic.


## r23
- Fixed appraisal matching so the dashboard accepts both the original appraisal API field names and the cleaned camelCase field names.
- Prevents valid visits appearing as 'Requires visit' when the API and frontend are briefly on different schema revisions.

## r24
- Officer profile image now uses declaration headshot first, then the latest appraisal/site-visit headshot, then the existing placeholder.
- Broken declaration image URLs automatically fall through to the appraisal headshot.
- Appraisal normalisation now accepts `headshot` and `fullBodyPhoto` (plus capitalised compatibility aliases).
- Latest appraisal full-body photo can be opened from the Appraisal / Site Visit section in a dedicated viewer.
- Existing compliance, incident and wallboard behaviour retained.

## r25
- Officer headshot thumbnail is now clickable.
- Clicking the headshot opens the image in the existing large photo viewer.
- Added a subtle zoom cursor/hover treatment so the thumbnail reads as interactive.

## r26
- Officers with no recorded appraisal now show `1st Visit Required` instead of `Requires visit`.
- Full-body photo action wording now makes the enlarge behaviour explicit and uses a zoom cursor.

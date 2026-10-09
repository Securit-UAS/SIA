# TALOS Master Compliance Dashboard

Revision 7 builds on the combined master compliance payload and adds module-level control and clearer SIA risk presentation.

The single Power Automate API payload is expected to contain `staff`, `sites`, the six training arrays, `declarations`, and `sia`. The web page joins those datasets by Staff ID and site.

Main register columns: Officer, Company / Provider, Site(s), Manager, SIA Status, Training Status, Declaration Status, PPAC Status.

## Compliance module toggles

SIA, Training and Declaration are enabled by default. PPAC is visible but disabled by default until a live PPAC data source is connected. Disabled modules remain visible but do not contribute to overall status, row colour or Critical/Review filtering. Toggle choices are remembered locally in the browser.

## SIA rules

- Expired or licence not found: red Critical.
- Red SIA records are always pushed to the top of the list and their row border pulses red, regardless of module toggle state.
- Material name mismatch, stale check, unrecognised licence sector, or expiry at 7 days or less: amber Review.
- Expiry at 8–30 days: blue Information.
- Accepted licence sectors: Security Guarding, Door Supervision and Close Protection.
- Otherwise: green All in order.

## Declaration rules

- Labour Provider staff: declaration required on every site.
- Direct SecurIT staff: declaration required only where any current SIA booking is an MCL/McLaren site.
- Direct SecurIT staff on non-MCL sites: declaration shows Not required (black).
- Labour Provider declared company is compared with the canonical Rolling Staff DB provider; material mismatch is amber.

## PPAC placeholder rules

- Direct SecurIT staff: Not Required unless currently deployed to a McLaren/MCL or Glencar site.
- Direct SecurIT staff on McLaren/MCL or Glencar: Not Found until PPAC is linked.
- Labour Provider staff: Not Found until PPAC is linked.
- PPAC is OFF by default, so these placeholder results do not affect overall compliance yet.

## Officer record

- SIA now has its own headline status badge.
- Officer headshot is shown top-right when available from the latest declaration.
- If no usable image is available, a fixed `Image not available` placeholder is shown.

The loading screen is paced over a 60-second window based on an observed API runtime of about 42 seconds.


## Revision 8
- Material SIA identity mismatches are now Critical/red even where the upstream C247 status is otherwise valid.
- Cosmetic capitalisation, ordering, or additional-name differences are tolerated when the names materially match.
- Critical identity mismatches inherit the existing top-of-register priority and pulsing red row treatment.

Revision 9
- Licence Not Found rows are the only rows with the pulsing red perimeter.
- Pulse is applied to the individual row cells so adjacent critical rows no longer appear as one grouped block.
- Sort order now prioritises Licence Not Found, then critical name mismatch / other critical SIA issues, then amber review items, then lower-severity records.


## Revision 11
- Compliance module toggles now also hide/show their corresponding status columns in the main officer register.
- Disabled modules continue to be excluded from overall status and row-colour calculations.
- Toggle preferences remain stored locally as before.

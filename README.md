# Securit SIA Compliance Dashboard

Full GitHub Pages site for the TALOS SIA Compliance dashboard.

This revision includes:
- severity sorting: red, amber, blue, green; alphabetical within each band
- row colour coding
- expiry alerting only at 31 days or less (blue 8–31, amber 0–7, red expired)
- case-insensitive name comparison to suppress capitalisation-only mismatch flags
- company/provider on headline rows
- Training Compliance linked by Staff ID
- responsible manager, training site and provider in View Record
- WhatsApp training links
- training certificate print/share controls
- shared Training/TALOS authentication session without displaying the unreliable auth displayName


Revision notes:
- Main register now shows separate SIA Status and Training Status columns with RAG dots.
- Role column removed from the headline table (role remains available in record details/filtering).
- Fully compliant SIA rows use normal white styling; colour wash is reserved for red/amber/blue exceptions.
.

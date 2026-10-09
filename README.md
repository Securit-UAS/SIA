# TALOS Master Compliance Dashboard

Revision 5 converts the original SIA dashboard into the master officer compliance view.

The single Power Automate API payload is expected to contain `staff`, `sites`, the six training arrays, `declarations`, and `sia`. The web page joins those datasets by Staff ID and site.

Main register columns: Officer, Company / Provider, Site(s), Manager, SIA Status, Training Status, Declaration Status.

Declaration rules currently implemented:
- Labour Provider staff: declaration required on every site.
- Direct SecurIT staff: declaration required only where any current SIA booking is an MCL/McLaren site.
- Direct SecurIT staff on non-MCL sites: declaration shows Not required (black).
- Labour Provider declared company is compared with the canonical Rolling Staff DB provider; material mismatch is amber.

The loading screen is paced over a 60-second window based on an observed API runtime of about 42 seconds.


Revision 6: combined API payload support, accepts either direct payload or Power Automate response wrapper. Packaged with site files at ZIP root for direct GitHub upload.

# Securit SIA Compliance

GitHub Pages front end for the TALOS SIA compliance dashboard.

Files:
- `index.html` — dashboard, shared Training-style login behaviour, filtering and officer detail view.
- `config.js` — Power Automate SIA API endpoint and shared TALOS auth endpoints.
- `securit-logo.png` — copied from the Training dashboard.

The page deliberately displays the authenticated **email address** rather than the auth service `displayName`, because the existing Training auth response is known to return the wrong display name for some users. This prevents that issue being carried into the SIA dashboard.

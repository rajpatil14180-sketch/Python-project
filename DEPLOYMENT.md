# GharPar deployment notes (.in domain)

The current ZIP is a local MVP. Do not point a public domain at the development server without completing the deployment hardening below.

## Local development

1. In PowerShell at the project root, run `py seed_data.py` only if you intentionally want to reset/create the demo database. It resets demo tables, so back up any real data first.
2. Start the API in one terminal: `py web_api.py`.
3. In a second terminal: `cd web`, then `npm install`, then `npm run dev`.
4. Open the Vite URL printed in the terminal. Demo owner: `owner` / `owner123`. Demo tenant accounts use the first name in lowercase (for example `amit`) and password `tenant123`.

## Hosting the purchased .in domain

A domain purchase does not include application hosting. You will also need a server/hosting provider and HTTPS. For the simplest deployment that preserves SQLite, use a small VPS with persistent disk:

1. Point the domain's DNS A record to the VPS IP. Add `www` as a CNAME or second A record if desired.
2. Build the React app with `npm ci` (once a lockfile exists) and `npm run build` inside `web/`.
3. Serve `web/dist/` as static files through a reverse proxy such as Nginx and configure HTTPS certificates.
4. Keep the Python API bound to `127.0.0.1:8765` behind the reverse proxy. Set `GHARPAR_WEB_ORIGIN` to the exact HTTPS origin, for example `https://example.in`, and supervise the Python process with systemd or the hosting provider's process manager.
5. Keep `pg.db` on persistent storage, back it up, and never place it inside a temporary build directory. Never commit the live database or credentials to GitHub.
6. Before using real tenant information, add production security hardening: persistent and expiring sessions, login rate limiting, CSRF/origin checks as appropriate, HTTPS-only transport, secret management, backup/restore testing, and an audit trail for payments and tenancy changes.

The standard-library HTTP server in `web_api.py` is suitable for the college MVP and local testing, not a hardened public production API by itself. Do not use real personal or payment records on a public deployment until the security checklist above is completed. For a hosted demo, use fake/sample data.

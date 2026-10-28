# GharPar PG Manager — Web MVP

This project keeps the original Python/Tkinter desktop application and adds a React/Vite web workspace using the same SQLite database and core business logic.

## Requirements

- Python 3.10 or newer
- Node.js and npm
- No Python packages are required

## Start locally on Windows

Open two PowerShell windows in the project root.

### Window 1: Python API

```powershell
py web_api.py
```

Keep the window open. The API listens at `http://127.0.0.1:8765` by default.

### Window 2: React web UI

```powershell
cd web
npm install
npm run dev
```

Open the local URL Vite prints, normally `http://127.0.0.1:5173`.

## Demo accounts

If you need the demo dataset, run `py seed_data.py` once before starting the API. **This resets the demo tables. Back up any real data first.**

- Owner: `owner` / `owner123`
- Tenant: `amit` / `tenant123`
- Other demo tenant usernames are first names in lowercase; their demo password is `tenant123`.

## MVP web features

- Owner login and property dashboard
- Property blueprint with clickable beds and bathroom labels
- Tenant directory, tenant details and historical payment records
- Add tenant with owner-editable suggested late-join price
- Record cash/UPI payments and vacate tenants without deleting their history
- Maintenance tickets, status updates and tenant ticket submission
- Announcements, including owner deletion
- Tenant portal with financial summary, payment history, announcements and maintenance requests

## Important hosting warning

The API is designed for local MVP development. Do not expose the standard-library development server directly to the public internet or store real tenant information on a public deployment until the production security checklist in `DEPLOYMENT.md` has been completed. A purchased domain is separate from web hosting. SQLite also requires persistent disk and a backup plan.

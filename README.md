# GharPar PG Manager

GharPar is a beginner-friendly PG management application built with Python, Tkinter, SQLite, and a React/Vite web workspace. Business rules remain in the existing Python core services; the web interface calls those services through `web_api.py`.

## Requirements

- Python 3.10 or newer
- Node.js and npm for the web interface
- No Python packages required

## Run the desktop app

```powershell
py seed_data.py
py main.py
```

`seed_data.py` resets the sample tables. Do not run it if you need to preserve real tenant/payment records.

## Run the web MVP

See [WEB_SETUP.md](WEB_SETUP.md) for the two-terminal setup and demo accounts.

## Run tests

```powershell
py -m unittest discover -s tests -v
```

## Hosting the .in domain

See [DEPLOYMENT.md](DEPLOYMENT.md). The current server is an MVP/local-development API and must be hardened before public use with real tenant data.

## MVP scope

Supports owner and tenant logins, two PGs with four rooms and eight beds each, late-join pricing, 12 installments, payment tracking, tenant history, maintenance tickets, and announcements. Reservations and tenant self-booking are intentionally excluded.

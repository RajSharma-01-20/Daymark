# Daymark — Personal Task Manager

Daymark is a standalone personal task manager. This edition keeps the standalone project's features and design while using a local single-user workspace. It has no sign-in, accounts, identity provider, or SSO flow.

## Features

- Inbox, Today, Upcoming, All Tasks, and Completed views
- Quick-add and editable tasks with notes, priorities, start and due dates
- Projects, tags, search, completion tracking, and preferences
- Local SQLite storage by default

## Run locally (PowerShell)

From the project root, prepare the Python environment and local configuration:

```powershell
py -m venv .venv
.\.venv\Scripts\Activate.ps1
py -m pip install -r backend\requirements.txt
Copy-Item .env.example .env
Copy-Item frontend\.env.example frontend\.env
```

Start the API in one terminal:

```powershell
uvicorn main:app --app-dir backend --reload --port 8101 --env-file .env
```

In a second terminal:

```powershell
Set-Location frontend
npm install
npm run dev -- --port 5174
```

Open http://localhost:5174. SQLite is used by default for local data. Set `DAYMARK_DATABASE_URL` in `.env` to use PostgreSQL. This project is designed for one local workspace. It does not authenticate users and should not be exposed to an untrusted network or shared between users.

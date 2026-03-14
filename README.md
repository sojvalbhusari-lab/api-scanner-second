# API Scanner

A small web app that generates a deterministic (seeded) API security scan report for a given URL.  
Backend: FastAPI. Frontend: static HTML/CSS/JS.

## Features
- POST a URL to generate a report with vulnerabilities, checks, and scores
- Retrieve reports by ID
- Deterministic results per URL (seeded RNG)

## Project Structure
- `backend/` FastAPI service
- `FRONTEND/` static UI pages

## Prerequisites
- Windows PowerShell
- Python 3.10+ (use the venv in `backend/venv/`)

## Backend: Run

From the repo root:

```powershell
backend\venv\Scripts\python -m uvicorn app:app --host 0.0.0.0 --port 8000 --app-dir backend
```

The API will be available at:
- `http://localhost:8000`
- Docs: `http://localhost:8000/docs`

## API

### Create a scan

```
POST /scan
Content-Type: application/json

{"url":"https://example.com"}
```

Response includes:
- `reportId`
- `report` (summary, vulnerabilities, checks, charts, suggestions)

### Fetch a report

```
GET /report/{reportId}
```

## Frontend

Open `FRONTEND/index.html` in a browser.  
If you host the frontend separately, ensure it points to the backend base URL.

## Notes

- Reports are stored in memory only. Restarting the backend clears them.


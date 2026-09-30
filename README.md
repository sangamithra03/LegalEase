# LegalEase-AI

LegalEase is an AI-powered legal document generator built with Streamlit, FastAPI, Gemini AI, and SQLite.

It helps users quickly draft professional legal documents such as agreements, contracts, and NDAs using simple form inputs and AI-generated content.

## Overview

- Streamlit (frontend)
- FastAPI (backend)
- Gemini AI (document generation)
- SQLite (saved document storage)
- DOCX / TXT / PDF export support

## 1. Create the environment

Windows (PowerShell):

```powershell
python -m venv venv
venv\Scripts\activate
```

macOS / Linux:

```bash
python3 -m venv venv
source venv/bin/activate
```

## 2. Install dependencies

```bash
pip install -r requirements.txt
```

## 3. Configure the API key

```bash
copy .env.example .env
```

Then edit `.env` and set your Gemini API key:

```env
GEMINI_API_KEY=your_api_key_here
```

You can get one at: https://aistudio.google.com/apikey

## 4. Run the app

Terminal 1:

```bash
uvicorn legalEaseAPI.main:app --reload
```

Terminal 2:

```bash
streamlit run frontend/app.py
```

Or use the project scripts:

- Windows: `run.bat`
- macOS/Linux: `run.sh`

## 5. Access the app

- API docs: http://localhost:8000/docs
- App UI: http://localhost:8501

The SQLite database file `legalease.db` is created automatically on first run.

## API Endpoints

- `POST /generate` — create and save a document
- `GET /documents` — list saved documents
- `GET /documents/{id}` — fetch one document
- `PUT /documents/{id}` — update edited content
- `DELETE /documents/{id}` — delete a document

## Deployment Notes

- Backend: `uvicorn legalEaseAPI.main:app --host 0.0.0.0 --port $PORT`
- Frontend: set `API_URL` to the deployed backend URL
- For temporary hosting environments, configure `DATABASE_URL` with a hosted PostgreSQL database

## Optional

Generate placeholder logos:

```bash
python create_logo.py
```

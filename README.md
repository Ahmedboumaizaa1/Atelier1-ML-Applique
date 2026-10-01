# Guichet ML

API that detects the language of a text (FastAPI), with a mock provider that works offline.

## Installation (Windows)

```
python -m venv .venv
.venv\Scripts\activate.bat
python -m pip install -r requirements.txt
copy .env.example .env
```

## Run

```
uvicorn app.main:app --reload
```

Then open http://127.0.0.1:8000/docs

## Tests

```
pytest -q
```
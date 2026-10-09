# Guichet ML

API FastAPI qui détecte la langue d'un texte (français, anglais, arabe).
Elle fonctionne hors ligne en mode MOCK ; un mode réel Hugging Face est optionnel.

## Installation (Windows PowerShell)

```powershell
py -m venv .venv
.venv\Scripts\Activate.ps1
python -m pip install --upgrade pip
python -m pip install -r requirements.txt
copy .env.example .env
```

Sous Linux ou WSL :

```bash
python3 -m venv .venv
source .venv/bin/activate
python -m pip install -r requirements.txt
cp .env.example .env
```

## Lancer l'API

```powershell
uvicorn app.main:app --reload
```

- Documentation interactive : http://127.0.0.1:8000/docs
- Santé : http://127.0.0.1:8000/health

## Exemple de requête

```powershell
$body = @{ text = "Je souhaite reinitialiser mon mot de passe." } | ConvertTo-Json
Invoke-RestMethod -Method Post -Uri "http://127.0.0.1:8000/detect-language" -ContentType "application/json" -Body $body
```

## Tests (hors ligne)

```powershell
pytest -q
```git status

## Codes de réponse

| Code | Signification |
|---|---|
| 200 | Réponse normale |
| 422 | Entrée invalide (texte trop court ou champ absent) |
| 503 | Fournisseur d'inférence indisponible |

## Configuration

Variables dans `.env` (jamais versionné) : `INFERENCE_MODE` (`mock` ou `real`), `HF_TOKEN`, `MODEL_ID`, `REVIEW_THRESHOLD`.
Ne jamais publier un jeton : s'il fuit, le révoquer.
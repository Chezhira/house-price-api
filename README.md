# 🏠 House Price Prediction API
[![CI](https://github.com/Chezhira/House-Price-Prediction-API/actions/workflows/ci.yml/badge.svg)](https://github.com/Chezhira/House-Price-Prediction-API/actions/workflows/ci.yml)

Production-grade **House Price Prediction** service using **CatBoost** and **FastAPI** — packaged, tested, and CI-enabled.

## Overview
This project serves a trained regression model behind a clean HTTP API for real-time inference. The goal is not only model performance, but **production readiness**:
- Reproducible Python packaging (`pyproject.toml`)
- Input validation (Pydantic)
- Automated tests (`pytest`)
- CI pipeline (GitHub Actions)

## Tech Stack
- Python 3.11+
- CatBoost (tabular regression)
- FastAPI (API layer)
- pytest + httpx (tests)
- GitHub Actions (CI)

## Project Structure
```text
.
├── src/
│   └── house_price_api/        # application package
├── tests/                      # automated tests (health + predict)
├── .github/workflows/ci.yml    # GitHub Actions workflow
├── pyproject.toml              # package + dependencies
└── README.md
Quickstart (Local)
Recommended (Conda)
# From repo root
conda create -n house_price_api python=3.11 -y
conda activate house_price_api

python -m pip install --upgrade pip
pip install -e ".[dev]"
pytest -q

Run the API

Start the server (from repo root):

uvicorn house_price_api.main:app --reload


Then open:

Swagger UI: http://127.0.0.1:8000/docs

Health: http://127.0.0.1:8000/health

If house_price_api.main:app doesn’t match your file name, use:

dir .\src\house_price_api


and replace main with the module that contains app = FastAPI().

API Endpoints
GET /health

Returns a simple status response to confirm the service is up.

POST /predict

Returns a price prediction for the provided feature payload.

The exact request schema is documented in Swagger UI:
http://127.0.0.1:8000/docs

Tests

Run all tests:

pytest -q

CI (GitHub Actions)

CI runs on pushes and PRs to main and executes:

pip install -e ".[dev]"

pytest -q

If CI fails with ModuleNotFoundError: httpx, ensure httpx is included in your dependency set (either main deps or dev extras).
<div align="center">

<img src="https://shieldcn.dev/header/gradient.svg?title=FastAPI%20for%20Machine%20Learning&subtitle=A%20small%20patient-record%20CRUD%20API%20for%20learning%20FastAPI&accent=%23009688&mode=dark" alt="FastAPI project banner" width="100%" />

![FastAPI](https://shieldcn.dev/badge/API-FastAPI-009688.svg?logo=fastapi&variant=secondary)
![Python](https://shieldcn.dev/badge/Python-3776AB.svg?logo=python&variant=secondary)
![Stars](https://shieldcn.dev/github/stars/Geetansh124/FastAPI-for-Machine-Learning.svg?variant=outline)

**A learning project demonstrating FastAPI, Pydantic models, query validation, and JSON-backed CRUD routes.**

[Source](https://github.com/Geetansh124/FastAPI-for-Machine-Learning) · [Issues](https://github.com/Geetansh124/FastAPI-for-Machine-Learning/issues)

</div>

> **Demo data only:** The API stores patient-shaped records in a local JSON file. Do not put real health information into this project or deploy it for clinical use; it has no authentication, authorization, audit controls, or production database.

## What the API demonstrates

`FastAPI/main.py` defines a Pydantic patient model with computed BMI and a category label, plus endpoints to list, view, sort, create, update, and delete records. Data is loaded from and written to `patients.json`. FastAPI also generates interactive API documentation from the route and model definitions.

~~~mermaid
flowchart LR
  C[HTTP client] --> A[FastAPI routes]
  A --> V[Pydantic validation]
  V --> J[(patients.json)]
  A --> C
~~~

## Run locally

~~~bash
git clone https://github.com/Geetansh124/FastAPI-for-Machine-Learning.git
cd FastAPI-for-Machine-Learning/FastAPI
python -m venv .venv
~~~

Activate the environment (`.venv\Scripts\Activate.ps1` in PowerShell or `source .venv/bin/activate` on macOS/Linux), then install and launch:

~~~bash
python -m pip install -r requirements.txt
uvicorn main:app --reload
~~~

Visit [http://127.0.0.1:8000/docs](http://127.0.0.1:8000/docs) to explore the OpenAPI UI. The API reads and writes `patients.json` relative to the working directory.

## Routes in the current source

| Method | Path | Purpose |
| --- | --- | --- |
| `GET` | `/` and `/about` | Simple informational responses |
| `GET` | `/view` | Return stored records |
| `GET` | `/patient/{patient_id}` | Retrieve one record |
| `GET` | `/sort` | Sort by height, weight, or BMI |
| `POST` | `/create` | Add a record after validation |
| `PUT` | `/edit/{patient_id}` | Update a record |
| `DELETE` | `/delete/{patient_id}` | Remove a record |

## Scope and safety

This is a small API-learning example, not a production health system or a machine-learning model. JSON-file persistence is not safe for concurrent writes or sensitive information. Use synthetic records, add tests and access controls, and replace the storage layer before any real-world deployment.

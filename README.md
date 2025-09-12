# Previsão de Preços de Combustíveis
## Objetivo

Construção de um pipeline MLOps open-source, de ponta a ponta, para previsão e análise de preços de combustíveis com dados da ANP e de postos de Goiânia.

## Arquitetura do Pipeline

Ingestão → coleta diária via API/scraping.

Camadas de dados → bronze → silver → gold.

Validação → Pandera/Great Expectations.

Feature engineering → atributos sazonais, médias móveis.

Treinamento → baseline regressão, rastreamento no MLflow.

Registro & Serving → MLflow Registry + API em FastAPI containerizada.

Orquestração → DAGs no Apache Airflow.

CI/CD → GitHub Actions (lint, testes, build, deploy).

Monitoramento → métricas e drift (Evidently, Prometheus).

Governança → Git, chaves SSH/GPG, pre-commit hooks, secrets management.

## Ferramentas

Infraestrutura: Docker, Kubernetes (kind/k3d), MinIO, Postgres

ML: scikit-learn, pandas, numpy, MLflow

Validação: Great Expectations, Evidently

APIs: FastAPI, Uvicorn

Orquestração: Airflow

CI/CD: GitHub Actions, pre-commit, gitleaks

## Estrutura Esperada

.github/workflows/ci.yaml # CI/CD
data/ # dados (mantido vazio via .gitkeep)
tests/unit/test_smoke.py # teste mínimo
requirements.txt # dependências
pyproject.toml # config de build
ruff.toml # lint

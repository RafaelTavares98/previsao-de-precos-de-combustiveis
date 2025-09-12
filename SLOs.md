# SLOs e Quality Gates — MLOps ANP Goiânia

## Serviço (API)
- Latência P95 < 150ms
- Uptime alvo (local de teste) >= 99%

## Modelo
- Gate relativo: rmse_novo <= 0.98 × rmse_baseline
- Gate absoluto (fallback): rmse_novo <= 0.25

## Dados (Great Expectations)
- Política: warning_ok_failure_block
- Mínimo de linhas por lote: 100

### Suites por camada
- bronze must-pass: row count mínimo, esquema válido
- silver must-pass: row count, esquema válido, regex de código ANP
- gold must-pass: esquema estável

## Operação
- DAG ingestão diária → success
- DAG treino semanal → success + quality gate aplicado
- DAG monitoramento diário → success + relatório Evidently

## Governança
- Commits assinados (GPG)
- Branch main protegida
- Segredos fora do Git; gitleaks limpo

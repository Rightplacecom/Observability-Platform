<<<<<<< HEAD
# Production-Grade Observability Platform

A containerized observability demonstration built with FastAPI, Prometheus, Grafana, Alertmanager, Node Exporter, cAdvisor, and Docker Compose.

## Services

| Service | URL |
|---|---|
| Application | http://localhost:8000 |
| Health | http://localhost:8000/health |
| Metrics | http://localhost:8000/metrics |
| Prometheus | http://localhost:9090 |
| Grafana | http://localhost:3000 |
| Alertmanager | http://localhost:9093 |
| cAdvisor | http://localhost:8080 |

## Quick Start

1. Copy the environment example:
   ```sh
   cp .env.example .env
   ```
2. Set a strong Grafana password in `.env`.
3. Start and validate the stack:
   ```sh
   docker compose config
   docker compose up -d --build
   ./scripts/validate_stack.sh
   ```
4. Open the URLs above. Grafana provisions its datasource and two dashboards automatically.

## Test the Application

```sh
pytest -q
curl http://localhost:8000/health
curl http://localhost:8000/metrics
```

## Incident Simulation

```sh
# Application health failure; recover with the same command using recover
./scripts/simulate_failure.sh error
./scripts/simulate_failure.sh recover

# Stop and restart the application container
./scripts/simulate_failure.sh app-down
./scripts/simulate_failure.sh app-up

# Bounded latency and CPU tests
curl "http://localhost:8000/simulate/latency?milliseconds=600"
curl "http://localhost:8000/simulate/cpu?seconds=5"

# HTTP 5xx generation
curl http://localhost:8000/simulate/error
```

Never run unbounded resource-exhaustion tests on shared systems.

## Alerting

Prometheus rules cover service availability, host CPU and memory, HTTP error rate, and request latency. Alertmanager routes firing/resolved notifications to the application's `/alerts` webhook for local demonstration.

Configure a secure external receiver and restricted administrative interfaces for any non-demo deployment.

## Runbooks

- [Service Down](runbooks/service-down.md)
- [High CPU](runbooks/high-cpu.md)
- [High Memory](runbooks/high-memory.md)
- [High Error Rate](runbooks/high-error-rate.md)

## Production Security

Use reviewed image versions, immutable deployment artifacts, TLS, authentication, network restrictions, persistent storage, secrets management, backup/restore procedures, and disaster-recovery testing before production use.
=======
# Observability-Platform
>>>>>>> 81dd353eb98e0600afd430eb5cbc90649c627c23

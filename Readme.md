# AirPure Hub Infrastructure

This repository contains the local development and Kubernetes configuration for AirPure Hub.

## Current Architecture

- `auth-service`: Node.js/Express service for registration, login, JWT issuing, and token verification.
- `logic-service`: Python/Flask service for AQI calculation and sensor reading processing.
- `io-service`: Go service that owns user and reading persistence APIs.
- `kong`: DB-less API gateway routing `/auth/*` to Auth and `/api/*` to Logic.
- `postgres`: user persistence database.
- `influxdb`: time-series target for processed air quality readings.
- `adminer`: database management UI.
- `prometheus` and `grafana`: monitoring and dashboard components.
- `portainer`: cluster/container management UI.
- Kubernetes `NetworkPolicy` resources isolate gateway, backend, database, observability, and management traffic.

## Local Development

The Compose file is kept for local validation and smoke testing:

```sh
docker compose -f docker-compose.yaml config
docker compose -f docker-compose.yaml build
docker compose -f docker-compose.yaml up
```

Gateway routes:

- `POST http://localhost:8000/auth/register`
- `POST http://localhost:8000/auth/login`
- `GET http://localhost:8000/auth/verify`
- `POST http://localhost:8000/api/process`
- `GET http://localhost:8000/api/history`

## Kubernetes

Manifests live in `k8s/airpure-hub.yaml` and include Deployments, Services, ConfigMaps, Secrets, PVCs, Kong, Adminer, Prometheus, Grafana, and Portainer.

The manifests use `nodeSelector` keys such as `airpure.io/tier=application`, `airpure.io/tier=database`, `airpure.io/tier=gateway`, and `airpure.io/tier=observability` as the Kubernetes equivalent of placement constraints.

Portainer uses a Kubernetes service account with cluster-admin access for cluster UI management. Grafana is provisioned with a Prometheus datasource and the AirPure Hub Overview dashboard.

Validation:

```sh
docker run --rm -v "$PWD:/work" ghcr.io/yannh/kubeconform:v0.6.7 -summary /work/k8s/airpure-hub.yaml
jq empty grafana/dashboards/*.json
```
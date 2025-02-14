# dre-test

> This repo contains a simple Airflow setup for testing purposes.

### Prerequisites

- Docker
- Docker Compose

### Usage

```bash
export AIRFLOW_UID=$(id -u)
docker compose up -d
```

### Airflow UI

```bash
http://localhost:8080
```

login with:

```bash
airflow
airflow
```
 
References:
- https://airflow.apache.org/docs/apache-airflow/stable/howto/docker-compose/index.html


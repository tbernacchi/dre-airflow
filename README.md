# dre-airflow

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

### Issues

```bash
[- ./dags:/opt/airflow/dags](../../blob/main/compose.yaml#L14)
[def smooth():](../../blob/main/dags/smooth.py#L12)
```

References:
- https://airflow.apache.org/docs/apache-airflow/stable/howto/docker-compose/index.html
- https://airflow.apache.org/docs/apache-airflow/stable/core-concepts/dags.html



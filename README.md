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
[`- ./dags:/opt/airflow/dags`](https://github.com/tbernacchi/dre-airflow/blob/0a7ab6dd9d52e783b730ca8c488a6b492eeef7f6/compose.yaml#L14)
[`def smooth():`](https://github.com/tbernacchi/dre-airflow/blob/main/dags/smooth.py#L12)
```

References:
- https://airflow.apache.org/docs/apache-airflow/stable/howto/docker-compose/index.html
- https://airflow.apache.org/docs/apache-airflow/stable/core-concepts/dags.html



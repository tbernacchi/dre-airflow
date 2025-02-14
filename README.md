# dre-airflow

> This repo contains a simple Airflow setup for testing purposes.

### Prerequisites

- Docker
- Docker Compose

### Issues

- Volume mapping in `compose.yaml`: [`- ./dags:/opt/airflow/dags`](https://github.com/tbernacchi/dre-airflow/blob/0a7ab6dd9d52e783b730ca8c488a6b492eeef7f6/compose.yaml#L14)
- Smooth function in DAG: [`def smooth():`](https://github.com/tbernacchi/dre-airflow/blob/main/dags/smooth.py#L12)

```bash
dre-airflow|main⚡ ⇒ docker compose up -d 
WARN[0000] The "AIRFLOW_UID" variable is not set. Defaulting to a blank string. 
[+] Running 3/3
 ✔ Container dre-airflow-redis-1         Healthy                                                                                                                                                                                                1.2s 
 ✔ Container dre-airflow-postgres-1      Healthy                                                                                                                                                                                                1.2s 
 ✘ Container dre-airflow-airflow-init-1  service "airflow-init" didn't complete successfully: exit 1                                                                                                                                           63.7s 
service "airflow-init" didn't complete successfully: exit 1

dre-airflow|main⚡ ⇒ docker compose logs airflow-init
...
...
...
airflow-init-1  |     conn = _connect(dsn, connection_factory=connection_factory, **kwasync)
airflow-init-1  | psycopg2.OperationalError: FATAL:  password authentication failed for user "airflow"
```

-   user `airflow` in `compose.yaml`: [POSTGRES_USER: airflow](https://github.com/tbernacchi/dre-airflow/blob/d6578a05fca3835700f69eaee43fa21b585c01e4/compose.yaml#L31C1-L32C1)

### Usage

```bash
cat << EOF > .env
AIRFLOW_UID=50000
AIRFLOW_GID=0
POSTGRES_USER=airflow
POSTGRES_PASSWORD=airflow
POSTGRES_DB=airflow
EOF

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

### References:
- https://airflow.apache.org/docs/apache-airflow/stable/howto/docker-compose/index.html
- https://airflow.apache.org/docs/apache-airflow/stable/core-concepts/dags.html


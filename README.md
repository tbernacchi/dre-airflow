# dre-airflow

> This repo contains a simple Airflow setup for testing purposes.

## Prerequisites

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

-   user `airflow` in `compose.yaml`: [POSTGRES_USER: airflow](https://github.com/tbernacchi/dre-airflow/blob/5c5676014d51f185d35bbfca61e59b830905796e/compose.yaml#L31C1-L32C1)

## Usage

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

## Airflow UI

```bash
http://localhost:8080
```

login with:

```bash
airflow
airflow
```

## Architecture

An Airflow installation generally consists of the following components:

* A scheduler, which handles both triggering scheduled workflows, and submitting Tasks to the executor to run.
* An executor, which handles running tasks. In the default Airflow installation, this runs everything inside the scheduler, but most production-suitable executors actually push task execution out to workers.
* A webserver, which presents a handy user interface to inspect, trigger and debug the behaviour of DAGs and tasks.
* A folder of DAG files, read by the scheduler and executor (and any workers the executor has)
* A metadata database, used by the scheduler, executor and webserver to store state.
A metadata database, used by the scheduler, executor and webserver to store state.

<div align=>
	<img align="center"  src=/.github/assets/img/arch-diag-basic.png>
</div>

## AWS proposed architecture

<div align=>
	<img align="center"  src=/.github/assets/img/airflow.drawio.png>
</div>

### <u>References</u>
- https://airflow.apache.org/docs/apache-airflow/stable/howto/docker-compose/index.html
- https://airflow.apache.org/docs/apache-airflow/stable/core-concepts/dags.html
- https://medium.com/@binayalenka/airflow-architecture-667f1cc613e8
- https://airflow.apache.org/docs/apache-airflow/2.5.3/core-concepts/overview.html
- https://airflow.apache.org/docs/apache-airflow/stable/core-concepts/overview.html#architecture-diagrams
- https://airflow.apache.org/docs/apache-airflow/stable/installation/index.html

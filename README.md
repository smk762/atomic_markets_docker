## Setup

Build container with `docker-compose build`
Launch container with `docker-compose up`
Create database tables with `./create_tables.py` in the "dexstats_sqlite_db" subfolder. To drop existing tables first, use `./create_tables.py drop_first`.

You'll need to setup a `.env` file with the values below in the root folder of this repository:

```
# External MySQL source DB
mysql_hostname="xx.xx.xx.xx"
mysql_username="user"
mysql_password="pass"
mysql_db="db_name"

# FastAPI
API_USER="user"
API_PASS="pass"

# Postgres/TimescaleDB
POSTGRES_HOST=localhost
POSTGRES_PORT=5432
POSTGRES_DATABASE=pg_db_name
PGDATA=/var/lib/postgresql/data
POSTGRES_USER=pg_username
POSTGRES_PASSWORD=pg_password

# AtomicDEX API 
MM2_USERPASS="rpc_password"
MM2_SEED="seed phrase or private key"
MM2_NETID=7777
MM2_GUI="MM2_Docker"
MM2_RPC_IP="0.0.0.0"
MM2_PORT=7783
MM2_RPC_LOCAL_ONLY="False"
MM2_I_AM_SEED="False"
MM2_SEEDNODES="80.82.76.214 89.248.168.39 89.248.173.231"

# Do not change the values below, they are used for internal container networking.
DOCKER_MM2_SERVICE_NAME="mm2"
DOCKER_REACT_SERVICE_NAME="dashboard"
DOCKER_DB_SERVICE_NAME="db"
DOCKER_API_SERVICE_NAME="fastapi"
```

A second .env file is also needed in the `atmicdex_markets` folder with a value for `REACT_APP_API_URL`. Set it to `http://127.0.0.1:8080"` for local testing.
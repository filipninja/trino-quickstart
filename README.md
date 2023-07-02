# trino-quickstart 

## Goal
Goal of this project is to quickly setup local persistent Trino environment. 
Components:
- Postgres database as storage engine for Hive Metastore
- Hive Metastore
- Trino with two catalogs using local file system:
  - Iceberg
  - Delta Lake

## Requirements
- Docker Compose
- Trino jdbc driver https://repo1.maven.org/maven2/io/trino/trino-jdbc/420/trino-jdbc-420.jar
- SQL Client (Datagrip, dbeaver, ...)

## Run
```shell
docker-compose up -d
```

## Configure client
- user: `admin`
- jdbc: `jdbc:trino://localhost:8080`

## Test
```sql
SHOW CATALOGS;
    
CREATE SCHEMA iceberg.test;     

CREATE TABLE iceberg.test.yearly_clicks (
    year,
    clicks
)
    WITH (
        partitioning = ARRAY['year']
)
AS VALUES
    (2021, 10000),
    (2022, 20000)
;    

SELECT * FROM iceberg.test.yearly_clicks;
```
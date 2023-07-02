# trino-quickstart 

## Goal
Goal of this project is to quickly setup local Trino development environment containing:
- Postgres database as storage engine for hive metastore
- Hive metastore
- Trino with two catalogs using local file system:
  - Iceberg
  - Delta lake

## Requirements
- docker-compose
- Trino jdbc driver https://repo1.maven.org/maven2/io/trino/trino-jdbc/420/trino-jdbc-420.jar
- sql client (Datagrip, dbeaver)

## Run
```
docker-compose up -d
```

## Configure client
- user: `admin`
- jdbc: `jdbc:trino://localhost:8080`

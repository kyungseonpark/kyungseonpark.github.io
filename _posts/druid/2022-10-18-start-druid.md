---
layout: post
read_time: true
show_date: true
title: Apache Druid Tutorial in Docker
date: 2022-10-18 12:29:12 -0600
description: Druid Tutorial in Docker
img: posts/cover/druid.webp
tags: [druid]
author: Kyungseon Park
github: kyungseonpark/
toc: yes
---

π<a href="https://druid.apache.org/docs/latest/tutorials/docker.html">Druid Tutorial in Docker μλ³Έ μΆμ²</a>

μ΅λν κ°λ°νκ²½μ μ μ½μ¬ν­ μμ΄ μ€ννκΈ° μν΄μ Docker Composeλ‘ μ€νν΄λ΄€μ΅λλ€.

# Docker compose YAML

π<a href="https://github.com/apache/druid/blob/24.0.0/distribution/docker/docker-compose.yml">Apache Druid 24.0.0, Docker compose YAML</a>

```yaml
version: "2.2"
volumes:
  metadata_data: {}
  middle_var: {}
  historical_var: {}
  broker_var: {}
  coordinator_var: {}
  router_var: {}
  druid_shared: {}
services:
  postgres:
    container_name: postgres
    image: postgres:latest
    volumes:
      - metadata_data:/var/lib/postgresql/data
    environment:
      - POSTGRES_PASSWORD=FoolishPassword
      - POSTGRES_USER=druid
      - POSTGRES_DB=druid
  # Need 3.5 or later for container nodes
  zookeeper:
    container_name: zookeeper
    image: zookeeper:3.5
    ports:
      - "2181:2181"
    environment:
      - ZOO_MY_ID=1
  coordinator:
    image: apache/druid:24.0.0
    container_name: coordinator
    volumes:
      - druid_shared:/opt/shared
      - coordinator_var:/opt/druid/var
    depends_on: 
      - zookeeper
      - postgres
    ports:
      - "8081:8081"
    command:
      - coordinator
    env_file:
      - environment
  broker:
    image: apache/druid:24.0.0
    container_name: broker
    volumes:
      - broker_var:/opt/druid/var
    depends_on: 
      - zookeeper
      - postgres
      - coordinator
    ports:
      - "8082:8082"
    command:
      - broker
    env_file:
      - environment
  historical:
    image: apache/druid:24.0.0
    container_name: historical
    volumes:
      - druid_shared:/opt/shared
      - historical_var:/opt/druid/var
    depends_on: 
      - zookeeper
      - postgres
      - coordinator
    ports:
      - "8083:8083"
    command:
      - historical
    env_file:
      - environment
  middlemanager:
    image: apache/druid:24.0.0
    container_name: middlemanager
    volumes:
      - druid_shared:/opt/shared
      - middle_var:/opt/druid/var
    depends_on: 
      - zookeeper
      - postgres
      - coordinator
    ports:
      - "8091:8091"
      - "8100-8105:8100-8105"
    command:
      - middleManager
    env_file:
      - environment
  router:
    image: apache/druid:24.0.0
    container_name: router
    volumes:
      - router_var:/opt/druid/var
    depends_on:
      - zookeeper
      - postgres
      - coordinator
    ports:
      - "8888:8888"
    command:
      - router
    env_file:
      - environment
```

# environment

π<a href="https://raw.githubusercontent.com/apache/druid/24.0.0/distribution/docker/environment">24.0.0 Docker environment</a>μμ μ‘°κΈ μμ ν νμΌμλλ€.

```shell
# Java tuning
DRUID_XMX=16g
DRUID_XMS=16g
DRUID_MAXNEWSIZE=8g
DRUID_NEWSIZE=8g
DRUID_MAXDIRECTMEMORYSIZE=16g
DRUID_SINGLE_NODE_CONF=micro-quickstart

druid_emitter_logging_logLevel=debug
druid_emitter_http_recipientBaseUrl=http://druid_exporter:8080/druid
druid_emitter=http

druid_extensions_loadList=["druid-kafka-indexing-service", "druid-multi-stage-query", "druid-parquet-extensions", "druid-avro-extensions", "druid-histogram", "druid-datasketches", "druid-lookups-cached-global", "postgresql-metadata-storage"]

druid_zk_service_host=zookeeper

druid_metadata_storage_host=
druid_metadata_storage_type=postgresql
druid_metadata_storage_connector_connectURI=jdbc:postgresql://postgres:5432/druid
druid_metadata_storage_connector_user=druid
druid_metadata_storage_connector_password=FoolishPassword

druid_coordinator_balancer_strategy=cachingCost

druid_indexer_runner_javaOptsArray=["-server", "-Xmx1g", "-Xms1g", "-XX:MaxDirectMemorySize=3g", "-Duser.timezone=UTC", "-Dfile.encoding=UTF-8", "-Djava.util.logging.manager=org.apache.logging.log4j.jul.LogManager"]
druid_indexer_fork_property_druid_processing_buffer_sizeBytes=512MiB

druid_storage_type=local
druid_storage_storageDirectory=/opt/shared/segments
druid_indexer_logs_type=file
druid_indexer_logs_directory=/opt/shared/indexing-logs

druid_processing_numThreads=2
druid_processing_numMergeBuffers=2

DRUID_LOG4J=<?xml version="1.0" encoding="UTF-8" ?><Configuration status="WARN"><Appenders><Console name="Console" target="SYSTEM_OUT"><PatternLayout pattern="%d{ISO8601} %p [%t] %c - %m%n"/></Console></Appenders><Loggers><Root level="info"><AppenderRef ref="Console"/></Root><Logger name="org.apache.druid.jetty.RequestLog" additivity="false" level="DEBUG"><AppenderRef ref="Console"/></Logger></Loggers></Configuration
```

μ¬κΈ°μ μ‘°κΈ ν¬μΈνΈλ₯Ό μ§μ΄λ³΄μλ©΄,

## JVM heap memory μ¬μ΄μ¦μ λν μ€μ λ€

```shell
# Java tuning
DRUID_XMX=16g
DRUID_XMS=16g
DRUID_MAXNEWSIZE=8g
DRUID_NEWSIZE=8g
DRUID_MAXDIRECTMEMORYSIZE=16g
DRUID_SINGLE_NODE_CONF=micro-quickstart
```

## Druid Extensions

- Druidμμλ μ¬λ¬κ°μ§ κΈ°λ₯λ€μ Extensionμ μ κ³΅ν©λλ€.
- π<a href="https://druid.apache.org/docs/latest/development/extensions.html">Druid extensions</a>

```shell
druid_extensions_loadList=["druid-kafka-indexing-service", "druid-multi-stage-query", "druid-parquet-extensions", "druid-avro-extensions", "druid-histogram", "druid-datasketches", "druid-lookups-cached-global", "postgresql-metadata-storage"]
```


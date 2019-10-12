# X2-server

## Overview

X2-server provides an official REST-API server which supports X2-API.

## Quick Start

Before running X2-server, backend server (Neo4j) is required to run.

Pull and run Neo4j Docker container.

```bash
mkdir -p $HOME/work/x2/neo4j/data # Add data about neo4j.
docker run \
  --publish=7474:7474 --publish=7687:7687 \
  --volume=$HOME/work/x2/neo4j/data:/data \
  -e NEO4J_AUTH=neo4j/neo4jtest \
  --name neo4j \
  neo4j:3.5.5                # 3.5.5 is the latest on Jun 2
```

`node` is pre-required.

```bash
git clone https://github.com/g2glab/x2
cd x2
yarn install
yarn build
yarn start
```

Access to `http://localhost:3000/`.

`http://localhost:3000/api-docs` provides a swagger-UI of this API definition.

## Configuration

`config/default.yaml` is the configuration file.

```yaml
db:
    dbms: "neo4j"
    protocol: "http"
    host: "http://localhost"
    port: 7474
    query: true
web:
    port: 3000
```

* db:
  * dbms(string): A backend graph database, i.e., "neo4j" or "pgx" (currently unsupported except for neo4j).
  * protocol(string): A way to connect to the backend graph, i.e., "http" or "bolt" or "java" (currently unsupported except for http).
  * host(string): A hostname which backend DBMS serves.
  * port(integer): A port for the backend DBMS. (Neo4j serves 7474 in default.)
  * query(boolean): Whether debugging queries are permitted.
* web:
  * port(integer): A port for serving web server. (Default: 3000)

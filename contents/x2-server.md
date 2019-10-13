# X2-server

## Overview

The X2-server provides an official REST-API server which supports the X2-API.

## Quick Start

In order to run the X2-server, Neo4j is required to run as a backend server.

Pull and run Neo4j Docker container.

```bash
mkdir -p $HOME/work/x2/neo4j/data # Add data-directory for neo4j
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

Access on `http://localhost:3000/`.

`http://localhost:3000/api-docs` provides a swagger-UI of this API definition.

## Configuration

`config/default.yaml` is the main configuration file (Docker-compose).

```yaml
db:
    dbms: "neo4j"
    protocol: "http"
    host: "http://localhost"
    port: 7474
    query: true
    auth:
      name: "neo4j"
      password: "neo4jtest"
      credential: ""
web:
    port: 3000
```

* db:
  * dbms(string): Backend graph database (currently only neo4j is supported)
  * protocol(string): Protocol for connecting to the backend DBMS (currently only http is supported)
  * host(string): Backend DBMS hostname
  * port(integer): Backend DBMS port (Neo4j: 7474 (default))
  * query(boolean): Permitting debugging queries
  * auth(optional): Authentication
    * name: User name (unsupported)
    * password: Password (unsupported)
    * credential: Credentials for basic auth
* web:
  * port(integer): Web server port (default: 3000)

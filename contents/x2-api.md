# X2-API

## Overview

* X2-API defines a set of endpoints with collected useful queries for visualizing graphs.
* X2 converts the output of queries into various graph database formats, including Neo4j, to a property graph exchange format called JSON-PG. 
* When an endpoint receives a request, the endpoint queries against the backend graph database with preset queries and then returns the JSON-PG format to the client.

## Interface

* GET /node_match: To retrieve subgraphs which consist of specified nodes.
  * [/node_match?node-id[]="id"]
  * [/node_match?node-label[]="label"]
  * [/node_match?node-prop[]="key;value"]
  * [/node_match?edge-id[]="id"]
  * [/node_match?edge-label[]="label"]
  * [/node_match?edge-prop[]="key;value"]
* GET /edge_match: To retrieve subgraphs which consist of specified edges.
  * [/edge_match?node-id[]="id"]
  * [/edge_match?node-label[]="label"]
  * [/edge_match?node-prop[]="key;value"]
  * [/edge_match?edge-id[]="id"]
  * [/edge_match?edge-label[]="label"]
  * [/edge_match?edge-prop[]="key;value"]
* GET /traversal: To retrieve a subgraph from another subgraph that consists of specified edges by traversing up to a given depth.
  * [/traversal?node-id[]="id"&iteration=2]
  * [/traversal?node-label[]="label"&iteration=2]
  * [/traversal?node-prop[]="key;value"&iteration=2]
  * [/traversal?edge-id[]="id"&iteration=2]
  * [/traversal?edge-label[]="label"&iteration=2]
  * [/traversal?edge-prop[]="key;value"&iteration=2]
* GET /query: To query to the backend DBMS directly (For debugging).
  * [/query?q=""]

See swagger API of X2-server in detail.

## Output Format

```json
{
    request: [],
    pg: {
        nodes: []
        edges []
    }
}
```

PG format is defined [here](https://pg-format.readthedocs.io/en/latest).

# X2-API

## Overview

* X2-API defines a set of endpoints with collected useful queries for visualizing graphs.
* X2 converts the output of queries into various graph database formats, including Neo4j, to a property graph exchange format called JSON-PG. 
* When an endpoint receives a request, the endpoint queries against the backend graph database with preset queries and then returns the JSON-PG format to the client.

## Interface

* GET /node_match: To retrieve subgraphs which consist of specified nodes.
  * [/node_match?node_ids[]="id"]
  * [/node_match?node_labels[]="label"]
  * [/node_match?node_props[]="key;value"]
  * [/node_match?edge_ids[]="id"]
  * [/node_match?edge_labels[]="label"]
  * [/node_match?edge_props[]="key;value"]
* GET /edge_match: To retrieve subgraphs which consist of specified edges.
  * [/edge_match?node_ids[]="id"]
  * [/edge_match?node_labels[]="label"]
  * [/edge_match?node_props[]="key;value"]
  * [/edge_match?edge_ids[]="id"]
  * [/edge_match?edge_labels[]="label"]
  * [/edge_match?edge_props[]="key;value"]
* GET /traversal: To retrieve a subgraph from another subgraph that consists of specified edges by traversing up to a given depth.
  * [/traversal?node_ids[]="id"&iteration=2]
  * [/traversal?node_labels[]="label"&iteration=2]
  * [/traversal?node_props[]="key;value"&iteration=2]
  * [/traversal?edge_ids[]="id"&iteration=2]
  * [/traversal?edge_labels[]="label"&iteration=2]
  * [/traversal?edge_props[]="key;value"&iteration=2]
* GET /compute/shortest: To retrieve a shortest path from another subgraph that 
  * [/compute/shortest?iteration=2&limit=1000&from_node_id="from_id"&to_node_id="to_id"]
  * [/compute/shortest?iteration=2&limit=1000&from_node_label="from_label"&to_node_label="to_label"]
  * [/compute/shortest?iteration=2&limit=1000&from_node_props[]="key;value"&to_node_props[]="key;value"]
* GET /profile: Fetch metadata of the graph
  * [/profile?profile_type="node"]  -- A list of node labels.
  * [/proifle?profile_type="edge"]  -- A list of edge labels.
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

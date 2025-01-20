# graphdb playground

This repository demonstrates how to work with Graph DB such as a Neo4j database. The setup includes defining schemas, inserting data, running queries, and performing graph algorithms in a GitHub Codespace.

[The Neo4j Cypher now accommodates most mandatory GQL features and a substantial portion of its optional ones.](https://neo4j.com/docs/cypher-manual/current/appendix/gql-conformance/)
Users should, therefore, only expect minimal differences between crafting queries in Cypher and GQL. 
For example, the following query is valid in both languages:  

```gql
MATCH (a:Actor)-[:ACTED_IN]->(m:Movie)
WHERE a.name = 'Tom Hanks'
RETURN m.title
```     

## Features

- **Graph Schema**: Define and model nodes and relationships.
- **Data Insertion**: Add nodes and relationships to the graph.
- **Querying Data**: Retrieve information using GQL queries.
- **Graph Algorithms**: Run algorithms like shortest path on the graph.

## Setup Instructions

### 1. Launch a Codespace

1. Navigate to this repository on GitHub.
2. Click the **Code** button and select **Codespaces**.
3. Click **Create codespace on main**.
4. Wait for the Codespace environment to initialize.

### 2. Environment Configuration

This repository uses a Dockerized Neo4j instance. The setup is pre-configured in:
- `.devcontainer/devcontainer.json`: Configures the GitHub Codespace environment.
- `docker-compose.yml`: Sets up Neo4j in a Docker container.

### 3. Access Neo4j

1. Once the Codespace is running, verify that the Neo4j container is active:
   ```bash
   sudo docker ps
   ```
2. Run the Neo4j:
   - `sudo docker exec -it gql_neo4j bash`
   - `cypher-shell -u neo4j -p strongpassword`
   
### 4. Run the GQL Examples

The `/examples` folder contains the following scripts:
- `schema.gql`: Defines the graph schema.
- `schema_properties.gql`: On how to access the graph schema.
- `data.gql`: Inserts data into the graph.
- `queries.gql`: Includes examples for querying data and running algorithms.

#### Steps to Run

1. Run the contents of `schema.gql` in the Neo4j.
2. Repeat the process for `data.gql` to populate the graph.
3. Execute the queries in `queries.gql` to explore the graph data.


---

## Repository Structure

```
.
├── .devcontainer/            # Codespace configuration files
│   └── devcontainer.json     # Devcontainer setup
├── docker-compose.yml        # Docker configuration for Neo4j
├── examples/                 # Folder containing GQL examples
│   ├── schema.gql            # Graph schema definition
│   ├── data.gql              # Graph data insertion
│   └── queries.gql           # GQL queries and algorithms
└── README.md                 # Project documentation
```

---

## Requirements

- **GitHub Codespaces** (or a local environment with Docker).
- **Neo4j**: Included via Docker Compose.
- **Browser**: To access the Neo4j interface.

---

## Getting Help

If you encounter any issues or have questions, feel free to create an [issue](https://github.com/your-username/gql-workflow-demo/issues) in this repository.

Happy querying! 🚀

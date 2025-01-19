# GQL Workflow Demo

This repository demonstrates how to work with Graph Query Language (GQL) using a Neo4j database. The setup includes defining schemas, inserting data, running queries, and performing graph algorithms in a GitHub Codespace.

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
   docker ps
   ```
2. Open the Neo4j browser:
   - Navigate to `http://localhost:7474` in the Codespace's browser.
   - Log in using the default credentials:
     - **Username**: `neo4j`
     - **Password**: `test`.

### 4. Run the GQL Examples

The `/examples` folder contains the following scripts:
- `schema.gql`: Defines the graph schema.
- `data.gql`: Inserts data into the graph.
- `queries.gql`: Includes examples for querying data and running algorithms.

#### Steps to Run

1. Copy the contents of `schema.gql` into the Neo4j browser query editor and run it.
2. Repeat the process for `data.gql` to populate the graph.
3. Execute the queries in `queries.gql` to explore the graph data.

---

## Example Queries

### Query: Friends of Alice

Retrieve all friends of Alice and the dates they became friends:
```gql
MATCH (a:Person)-[f:FRIEND]->(friend:Person)
WHERE a.name = "Alice"
RETURN friend.name AS Friend, f.since AS Since;
```

### Query: Mutual Friends

Find mutual friends between Alice and Bob:
```gql
MATCH (a:Person)-[:FRIEND]->(common:Person)<-[:FRIEND]-(b:Person)
WHERE a.name = "Alice" AND b.name = "Bob"
RETURN common.name AS MutualFriend;
```

### Query: Shortest Path
Find the shortest path between Alice and Charlie:
```gql
MATCH path = shortestPath((a:Person)-[:FRIEND*]->(c:Person))
WHERE a.name = "Alice" AND c.name = "Charlie"
RETURN path;
```

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
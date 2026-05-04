---
title: "CS224W: Machine Learning with Graphs — Learning Notes (Updating)"
date: 2026-05-03
categories: [Notes, Machine Learning]
tags: [graphs, ml]
math: true
---

> **Course:** [Stanford CS224W (Winter 2021)](https://www.youtube.com/playlist?list=PLoROMvodv4rPLKxIpqhjhPgdQy7imNkDn)

> **Instructor:** Prof. Jure Leskovec

> **Lectures Covered:** 1.1 – 2.3 (Traditional Feature-based Methods)



# 1. Introduction to Graph ML

## 1.1 — Why Graphs?

Many real-world data naturally live on graphs, simply, entities connected by relationships. Rather than treating data points as isolated, graphs let us model the rich structure of interactions between them.

**Key motivation:** Complex systems in biology, society, technology, and science can all be described as networks of interconnected entities. Graphs give us a universal mathematical language to reason about these systems.

**Examples of networks:**
- Social networks (friendships, followers)
- Communication networks (emails, phone calls)
- Biological networks (protein interactions, gene regulation, disease pathways)
- Information networks (the Web, citation graphs)
- Infrastructure networks (roads, power grids)

**Why ML on graphs?** Traditional ML assumes data points are independent (i.i.d.), but graph-structured data violates this — nodes are linked and influence each other. Graph ML lets us exploit relational structure to make better predictions.

**Types of tasks we can perform:**
- **Node-level:** Classify or predict properties of individual nodes (e.g., categorise a user)
- **Link-level:** Predict whether a link exists or will form between two nodes (e.g., friend recommendation)
- **Graph-level:** Classify or predict properties of entire graphs (e.g., predict molecular properties)



## 1.2 — Choice of Graph Representation

Before doing ML, we need to decide *how* to represent a graph. 

**Components of a graph G = (V, E):**
- **V** — set of nodes (vertices)
- **E** — set of edges (links)

**Types of graphs:**

| Property | Options |
|---|---|
| Edge direction | Undirected vs. Directed |
| Edge weight | Unweighted vs. Weighted |
| Self-loops | Allowed or not |
| Multigraph | Single edge vs. multiple edges between same pair |
| Bipartite | Nodes split into two disjoint sets, edges only between sets |

**Adjacency matrix A:** An N × N matrix where $A_{i,j} = 1$ if there is an edge from node i to node j. For undirected graphs, A is symmetric. Real-world graphs are typically *sparse* (most entries are 0), so the adjacency matrix is mostly zeros.

**Other representations:**
- **Edge list:** List of (source, target) pairs, compact for sparse graphs.
- **Adjacency list:** For each node, store a list of its neighbours.

**Key properties:**
- **Node degree $k_{i}$:** number of edges touching node i. For directed graphs, we distinguish in-degree and out-degree.
- Average degree of an undirected graph:$$\bar{k} = \frac{2|E|}{|V|}$$
- **Connectivity:** A graph is connected if there is a path between every pair of nodes. 
    - A directed graph is **strongly connected** if there is a valid path from every node to every other node, strictly following the direction of the edges.
    - A directed graph is **weakly connected** if it is not strongly connected, but it would be connected if treating all one-way arrows as two-way lines.









# 2. Traditional Feature-based Methods

The traditional ML pipeline on graphs has two steps:
1. Hand-design features that describe nodes, links, graphs;
2. Feed these features into a standard ML model (logistic regression, SVM, random forest, etc.). 

The notes below cover what features to design at each level.

> For simplicity, all discussion below assumes **undirected graphs** unless stated otherwise.


## 2.1 — Node-Level Features

**Goal:** Characterise the structure and position of a single node in the network.

### 1. Importance-based features

**i) Node Degree (Degree Centrality)** counting the number of edges the node has.

A node is important if the node has more connections, meaning it's critcial to the flow of the network.

$$k_v = |N(v)|$$

, where $N(v)$ is the set of neighbours of the node $v$. 

Limitation: treats all neighbours equally.

**ii) Node Centrality** measuring how *important* a node is within the graph. 

*   **Eigenvector Centrality**
    
    A node is important if its neighbours are important (recursive definition).

    $$c_v = \frac{1}{\lambda} \sum_{u \in N(v)} c_u$$

    This leads to the eigenvector equation **Ac = λc**. We take the eigenvector corresponding to the largest eigenvalue $λ_{max}$.

*   **Betweenness Centrality**
    
    A node is important if it lies on many shortest paths between other nodes.

    $$c_v = \sum_{s \neq v \neq t} \frac{\text{\# shortest paths between } s \text{ and } t \text{ that pass through } v}{\text{\# shortest paths between } s \text{ and } t}$$

    Captures "bridge" nodes.

*   **Closeness Centrality**

    A node is important if it has short shortest-path distances to all other nodes.

    $$c_v = \frac{1}{\sum_{u \neq v} d(v, u)}$$

    , where d(v, u) is the shortest path length from v to u. 
    
    High closeness = the node can reach everyone quickly.

### 2. Structure-based features

Focus on capturing *topological properties* of the graph, and how nodes are embedded with their local neighbours, regardless of what the nodes actually represent.

**i) Node Degree** defines the exact size of a node's immediate neighbours (1-hop ego-graph).

Distinguishes topological roles, e.g. the node is a "central hub", or a "bridge", or an "isolated leaf"


**ii) Clustering Coefficient** measuring how connected a node's neighbours are to each other. i.e., how "cliquish" the local neighbourhood is.

$$
\begin{aligned}
e_{v} &= \frac{\text{\# edges among neighbours of } v}{\text{\# node pairs among neighbours of } v} \\[1em]
&= \frac{\text{\# triangles}}{\binom{k_v}{2}} \in [0, 1]
\end{aligned}
$$

, where $k_{v}$ is the degree of $v$. 

Ranges from 0 (no edges among neighbours) to 1 (neighbours form a complete clique).

Essentially counts the fraction of triangles that *could* exist around node $v$ that actually do.

**iii) Graphlet Degree Vector (GDV):** A vector that counts, for each graphlet position, how many times node $v$ appears in that position, generalising the notion of counting triangles in the **Clustering Coefficient** by counting *all* small subgraph patterns (graphlets) that a node participates in. 

This provides a rich, detailed signature of a node's local network topology.

*   **Graphlets** are small, *rooted connected*, non-isomorphic subgraphs. 

*   A **single graphlet** has one specific, fixed graph structure.

*   **Non-isomorphic** means for every graphlet in the whole dictionary has a completely *unique* topological shape from all others.



### 3. Comparison of node features:

| Feature | What it captures |
|---|---|
| Degree | How many connections |
| Centrality | Importance / position in global structure |
| Clustering coefficient | Local triangle density |
| GDV | Detailed local topology (generalises clustering coeff.) |





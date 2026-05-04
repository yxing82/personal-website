---
title: "Learning Notes on Machine Learning with Graphs (Updating)"
date: 2026-05-03
categories: [Notes, Machine Learning]
tags: [graphs, ml]
math: true
---

> **Course:** [Stanford CS224W (Winter 2021)](https://www.youtube.com/playlist?list=PLoROMvodv4rPLKxIpqhjhPgdQy7imNkDn)

> **Instructor:** Prof. Jure Leskovec

> **Lectures Covered:** 1.1 – 2.3 (Traditional Feature-based Methods)

<br>
<br>
<br>

# 1. Introduction to Graph ML

<br>

## 1.1 Why Graphs?

Many real-world data naturally live on graphs, simply, entities connected by relationships. Rather than treating data points as isolated, graphs let us model the rich structure of interactions between them.

**Key motivation:** Complex systems in biology, society, technology, and science can all be described as networks of interconnected entities. Graphs give us a universal mathematical language to reason about these systems.

**Examples of networks:**
- Social networks (friendships, followers)
- Communication networks (emails, phone calls)
- Biological networks (protein interactions, gene regulation)
- Information networks (the Web, citation graphs)
- Infrastructure networks (roads, power grids)

**Why ML on graphs?** Traditional ML assumes data points are independent (i.i.d.), but graph-structured data violates this — nodes are linked and influence each other. Graph ML lets us exploit relational structure to make better predictions.

**Types of tasks we can perform:**
- **Node-level:** Classify or predict properties of individual nodes (e.g., categorise a user)
- **Link-level:** Predict whether a link exists or will form between two nodes (e.g., friend recommendation)
- **Graph-level:** Classify or predict properties of entire graphs (e.g., predict molecular properties)



## 1.2 Choice of Graph Representation

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

**Adjacency matrix $A$:** An N × N matrix where $A_{i,j} = 1$ if there is an edge from node i to node j. 

For undirected graphs, A is symmetric. i.e. $A_{i,j} = A_{j,i}$ and $A_{i,i} = 0$

Real-world graphs are typically *sparse* (most entries are 0), so the adjacency matrix is mostly zeros.

**Other representations:**
- **Edge list:** List of (source, target) pairs, compact for sparse graphs.
- **Adjacency list:** For each node, store a list of its neighbours.

**Key properties:**
- **Node degree $k_{i}$:** number of edges touching node i. For directed graphs, we distinguish in-degree and out-degree.
- Average degree of an undirected graph:
$$\bar{k} = \frac{2|E|}{|V|}$$
- **Connectivity:** a graph is connected if there is a path between every pair of nodes. 
    - a directed graph is **strongly connected** if there is a valid path from every node to every other node, strictly following the direction of the edges.
    - a directed graph is **weakly connected** if it is not strongly connected, but it would be connected if treating all one-way arrows as two-way lines.

<br>
<br>
<br>

# 2. Traditional Feature-based Methods

The traditional ML pipeline on graphs has two steps:
1. Hand-design features that describe nodes, links, graphs;
2. Feed these features into a standard ML model (logistic regression, SVM, random forest, etc.). 

The notes below cover what features to design at each level.

> For simplicity, all discussion below assumes **undirected graphs** unless stated otherwise.

<br>

## 2.1 Node-Level Features

**Goal:** Characterise the structure and position of a single node in the network.

### 1. Importance-based features

Measures how important the node is.

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

    $$c_v = \sum_{s \neq v \neq t} \frac{\text{# shortest paths between } s \text{ and } t \text{ that pass through } v}{\text{# shortest paths between } s \text{ and } t}$$

    Captures "bridge" nodes.

*   **Closeness Centrality**

    A node is important if it has short shortest-path distances to all other nodes.

    $$c_v = \frac{1}{\sum_{u \neq v} d(v, u)}$$

    , where d(v, u) is the shortest path length from v to u. 
    
    High closeness = the node can reach everyone quickly.

### 2. Structure-based features

Captures *topological properties* of the graph, and how nodes are embedded with their local neighbours, regardless of what the nodes actually represent.

**i) Node Degree** defines the exact size of a node's immediate neighbours (1-hop ego-graph).

Distinguishes topological roles, e.g. the node is a "central hub", or a "bridge", or an "isolated leaf"


**ii) (Local) Clustering Coefficient** measuring how connected a node's neighbours are to each other. 

The fundamental building block is the **triangle**. If node $v$ is connected to both $u$ and $w$, a triangle is **"closed"** when $u$ and $w$ are also connected. Then the **(local) Clustering Coefficient** measures what fraction of a node's neighbour pairs actually **close the triangle**:

$$
\begin{aligned}
e_{v} &= \frac{\text{# edges among neighbours of } v}{\text{# node pairs among neighbours of } v} \\[1em]
&= \frac{\text{# triangles}}{\binom{k_v}{2}} \in [0, 1]
\end{aligned}
$$

, where $k_{v}$ is the degree of $v$. 

Ranges from 0 (no edges among neighbours) to 1 (neighbours form a complete clique).

*   **Problems with Bipartite Graphs:** 
    *   Triangles can NEVER form: if $u_{1} \in U$ connects to $v_{1} \in V$ and $v_{2} \in V$, the edge $(v_{1}, v_{2})$ cannot exist because both are in the same set $V$.

        The standard Clustering Coefficient is then always **zero** for every node in a bipartite graph

*   **Bipartite Clustering Coefficient (4-Cycles / Squares):** counts 4-cycle (square) as a closed path $u_{1} \rightarrow v_{1} \rightarrow u_{2} \rightarrow v_{2} \rightarrow u_{1}$, where $u_{1}, u_{2} \in U$ and $v_{1}, v_{2} \in V$. 

$$cc_v = \frac{\text{# closed 4-cycles through } v}{\text{# possible 4-cycles through } v}$$

*   
    | Graph type | Smallest cycle | Clustering measures |
    |---|---|---|
    | General (unipartite) | Triangle (3-cycle) | Standard clustering coefficient |
    | Bipartite | Square (4-cycle) | Bipartite clustering coefficient |



**iii) Graphlet Degree Vector (GDV):** A vector that counts, for each graphlet position, how many times node $v$ appears in that position, generalising the notion of counting triangles in the **Clustering Coefficient** by counting *all* small subgraph patterns (graphlets) that a node participates in. 

This provides a rich, detailed signature of a node's local network topology.

*   **Graphlets** are small, *rooted connected*, non-isomorphic subgraphs. 

*   A **single graphlet** has one specific, fixed graph structure.

*   **Non-isomorphic** means for every graphlet in the whole dictionary has a completely *unique* topological shape from all others.



### Comparison of node features:

| Feature | What it captures |
|---|---|
| Degree | How many connections |
| Centrality | Importance / position in global structure |
| Clustering coefficient | Local triangle density |
| GDV | Detailed local topology (generalises clustering coeff.) |


<br>

## 2.2 Link-Level Features

**Goal:** Design features for a *pair* of nodes $(v_{1}, v_{2})$ to predict whether a link exists or will form between them.

### 1. Distance-Based Features

Use the **shortest-path distance** between $v_{1}$ and $v_{2}$, meaning how likely nodes can be connected.

Limitation: this only captures path length, not the *richness* of the connection (degree information, e.g. two nodes at distance 2 might share 1 or 100 common neighbours).

### 2. Local Neighbourhood Overlap

Captures how many neighbours are shared between two nodes. More overlap means more likely to be linked.

**i) Common Neighbours** simply counts how many nodes are neighbours of both $v_{1}$ and $v_{2}$.

$$|N(v_1) \cap N(v_2)|$$


**ii) Jaccard Coefficient** normalises common neighbours by the total size of both neighbourhoods. Gives a proportion rather than a raw count.

$$\frac{|N(v_1) \cap N(v_2)|}{|N(v_1) \cup N(v_2)|}$$


**iii) Adamic-Adar Index** weights each common neighbour by the inverse log of its degree. 

$$\sum_{u \in N(v_1) \cap N(v_2)} \frac{1}{\log(k_u)}$$

The intuition: a shared neighbour who is very popular (high degree) is less meaningful than one with few connections. If two people both know a celebrity, that's less significant than if they both know the same niche researcher.

**Limitation of local features:** If two nodes have no common neighbours, all these features are zero, even if the nodes are structurally very similar or destined to connect.

### 3. Global Neighbourhood Overlap

Considers the entire graph, not just immediate neighbourhoods.

**Katz Index** counts the number of paths of *all lengths* between two nodes, with shorter paths weighted more heavily:

$$S_{v_1, v_2} = \sum_{l=1}^{\infty} \beta^l \cdot \mathbf{A}^l_{v_1, v_2}$$

, where:
- **$A$** is the adjacency matrix
- **$A^l$** gives the number of paths of length l between nodes
- **β ∈ (0, 1)** is a discount factor that exponentially downweights longer paths

In closed form: **S = (I − βA)⁻¹ − I**.

To break down this complicated form, let $P^{(k)}_{uv} = \text{\# paths of length k between nodes u and v}$,

*   Given adjacency matrix $A$, we can directly have $P^{(1)}_{uv} = A_{uv}$.

*   For length 2, we multiply the adjacency matrix $A$ with itself, and derive $P^{(2)}_{uv} = A_{uv} * A_{uv} = A^{2}_{uv}$.

    $$(A^2)_{uv} = \sum_{w=1}^{|V|} A_{uw} A_{wv}$$
    
    *   $A_{uw}$: Is there an edge from node $u$ to an intermediate node $w$? (1 if yes, 0 if no).
    *   $A_{wv}$: Is there an edge from that same intermediate node $w$ to the destination node $v$? (1 if yes, 0 if no).
    *   $\sum$: By summing over every possible intermediate node $w$ in the entire graph (from $1$ to $\vert V \vert$), we count how many two-step paths exist between $u$ and $v$.




The Katz index resolves the limitation of local methods by capturing indirect connections through the entire network.

### Summary of link features:

| Feature type | Examples | Scope |
|---|---|---|
| Distance-based | Shortest path | Global but coarse |
| Local overlap | Common neighbours, Jaccard, Adamic-Adar | Local (immediate neighbours only) |
| Global overlap | Katz index | Global (all paths) |

<br>

## 2.3 Graph-Level Features

**Goal:** Create a feature vector that describes an *entire graph*, enabling graph-level classification.

### Kernel Methods

Instead of explicitly designing a feature vector $\phi(G)$, we can define a **graph kernel** $K(G, G')$ that measures the similarity between two graphs. By the kernel trick, there implicitly exists some feature map $\phi$ such that:

$$K(G, G') = \phi(G)^T \phi(G')$$

This lets us use kernel-based ML methods (SVM, etc.) without ever computing $\phi$ explicitly.

**Key idea:** **Bag-of-\*** represents a graph by counts of certain substructures, ignoring order.

### 1. Graphlet Kernel

Represent a graph by counting the number of each type of **graphlet** it contains.

Steps:
1. Enumerate all graphlets up to $k$ (e.g., $k$ = 3, 4, or 5 nodes).
2. For each graphlet type, count how many times it appears as a subgraph of $G$.
3. This count vector is the graph's feature vector.

The definition of **graphlets at the graph-level** do **not** need to be connected and are **not** rooted at a specific node, which is different from node-level graphlets.

**Normalisation:** If comparing graphs of different sizes, normalise the count vectors (e.g., by the total count) so that large graphs don't dominate.

**Limitation:** Counting graphlets is computationally expensive.

### 2. Weisfeiler-Lehman (WL) Kernel

Use an iterative neighbourhood aggregation (**colour refinement**) scheme to build up a vocabulary of "colours" that encode local structure, then count these colours. This is a much more efficient alternative to the graphlet kernel.

**Colour Refinement Algorithm:**

1. **Initialise:** Assign every node the same colour (or use node labels if available).
2. **Iterate:** For each node, create a new colour by **hashing** together its current colour and the *multiset* of colours of its neighbours.
3. **Repeat** for K iterations. After K steps, each node's colour summarises the structure of its K-hop neighbourhood.

After colour refinement, represent each graph as a count vector of how many nodes have each colour. The WL kernel between two graphs is then the dot product of their colour count vectors.

**Why this works:** The colour refinement process is essentially a generalisation of counting node degrees:
- After 1 iteration, a node's colour encodes its degree (1-hop info).
- After 2 iterations, it encodes the degrees of its neighbours (2-hop info).
- After K iterations, it encodes the full K-hop neighbourhood structure.

**Advantages over graphlet kernel:**
- Computationally efficient: each iteration is linear in the number of edges.
- Only requires K iterations (typically small, e.g., 3–5).
- Captures increasingly rich structural information with each iteration.

**Other graph kernels** (mentioned but not covered in detail):
- Random walk kernel
- Shortest-path graph kernel

<br>
<br>
<br>

# Summary: The Traditional ML Pipeline on Graphs

**What covered:**

| Level | Features | Key Concepts |
|---|---|---|
| **Node** | Degree, centrality, clustering coeff., GDV | Capture importance and local topology |
| **Link** | Shortest path, common neighbours, Jaccard, Adamic-Adar, Katz | Capture pairwise proximity and overlap |
| **Graph** | Graphlet kernel, WL kernel | Capture global substructure patterns |

**Key limitation of traditional methods:** All features are hand-designed. This requires domain knowledge and doesn't automatically learn representations from data. 

The rest of the course (Lectures 3+) addresses this by introducing methods that *learn* features automatically, starting with node embeddings and moving to graph neural networks.


# Modularity on the Karate Club Graph

**Course:** DSC212 – Graph Theory 
**Name:** Divyansh Trivedi  
**Roll Number:** IMS25073  
**Institute:** IISER Thiruvananthapuram

---

## 1. Project Overview

This project implements **spectral modularity-based community detection** on Zachary's Karate Club graph using Python.

The objective is to identify groups of closely connected nodes by studying the network's modularity structure. The implementation follows the recursive spectral bisection approach described in Newman (2006).

The project explores how linear algebra and graph theory can be combined to identify community structures in social networks.

## 2. Objectives

The assignment focuses on the following tasks:

- Construct the adjacency matrix, degree vector, and global modularity matrix of the Karate Club graph.
- Implement recursive spectral bisection using eigenvalue decomposition.
- Identify communities through the signs of the leading eigenvector.
- Visualize the network after successive community splits.
- Study the evolution of node-level network metrics across iterations.
- Interpret how community fragmentation influences network structure and node centrality.

## 3. Dataset

The project uses the **Zachary Karate Club graph**, available directly through NetworkX.

The graph represents friendship interactions among 34 members of a university karate club.

| Property | Value |
|---|---:|
| Number of nodes | 34 |
| Number of edges | 78 |
| Graph type | Undirected |
| Edge representation | Unweighted |

The graph is initialized using:

```python
G = nx.karate_club_graph()
```

## 4. Mathematical Methodology

### 4.1 Global Modularity Matrix

The global modularity matrix is constructed as

$$
B = A - \frac{\mathbf{k}\mathbf{k}^{\top}}{2m}
$$

where:

- $A$ is the adjacency matrix.
- $\mathbf{k}$ is the degree vector.
- $m$ is the total number of edges.

The expected-edge matrix provides a null-model baseline

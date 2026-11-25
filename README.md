# Modularity on the Karate Club Graph

**Course:** DSC212 – Graph Theory<br>
**Name:** Divyansh Trivedi<br>
**Roll Number:** IMS25073<br>
**Institute:** IISER Thiruvananthapuram<br>

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

| Property            |      Value |
| ------------------- | ---------: |
| Number of nodes     |         34 |
| Number of edges     |         78 |
| Graph type          | Undirected |
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

The expected-edge matrix provides a null-model baseline against which the observed connections are compared.

### 4.2 Spectral Bisection

The modularity optimization problem is relaxed into a continuous optimization problem.

The leading eigenvector of the modularity matrix provides the basis for assigning nodes to two groups.

For a candidate community $C$, the restricted matrix is obtained by extracting the corresponding rows and columns directly from the global modularity matrix:

$$
B^{(C)} = B[C,C]
$$

The leading eigenpair is calculated using:

```python
eigenvalues, eigenvectors = np.linalg.eigh(B_C)
```

The community is considered for splitting when its largest eigenvalue exceeds the prescribed threshold:

$$
\lambda\_{\max}^{(C)} > 10^{-10}
$$

Nodes are assigned according to the sign of the leading eigenvector:

$$
s_i =
\begin{cases}
+1, & u_i > 0\\
-1, & u_i \leq 0
\end{cases}
$$

This process is repeated recursively until no further valid split is accepted.

## 5. Network Metrics

After each successful split, the network is updated to reflect the current community partition. The following four NetworkX metrics are calculated for every node:

| Metric                 | Purpose                                                               |
| ---------------------- | --------------------------------------------------------------------- |
| Degree Centrality      | Measures the direct connectivity of a node.                           |
| Betweenness Centrality | Measures how frequently a node acts as a bridge along shortest paths. |
| Closeness Centrality   | Measures how efficiently a node can reach other nodes.                |
| Clustering Coefficient | Measures the local connectivity among a node's neighbours.            |

The evolution of these metrics is plotted across successive iterations to examine changes in network structure and node importance.

## 6. Visualizations

The notebook includes:

- Network visualizations after successive community splits.
- Distinct colours to represent different communities.
- Node ID labels for identifying individual vertices.
- Metric evolution plots arranged in a 2 × 2 subplot grid.
- Comparative analysis of important nodes across iterations.

A fixed spring-layout seed is used to maintain consistent node positions across network visualizations.

## 7. Technologies and Libraries

The implementation uses:

- **Python** – Main programming language.
- **NumPy** – Matrix operations and eigenvalue decomposition.
- **NetworkX** – Graph construction and network metric calculations.
- **Matplotlib** – Network and metric visualizations.
- **Jupyter Notebook** – Interactive execution and presentation.

No built-in community detection algorithm is used; the spectral bisection procedure is implemented directly.

## 8. How to Run

Clone the repository:

```bash
git clone https://github.com/Divyansh-DT-19/Karate_Club_Graph.git
```

Navigate to the project directory:

```bash
cd Karate_Club_Graph
```

Install the required dependencies:

```bash
pip install numpy networkx matplotlib jupyter
```

Launch Jupyter Notebook:

```bash
jupyter notebook
```

Open `DSC212_Assignment_Divyansh_Trivedi.ipynb` and execute the cells sequentially from top to bottom.

## 9. Repository Structure

```text
Karate_Club_Graph/
│
├── DSC212_Assignment_Divyansh_Trivedi.ipynb
└── README.md
```

## 10. AI Usage Disclosure

AI assistance was used during this assignment to understand advanced technical aspects of the problem with which I was not previously familiar.

In particular, it helped clarify the mathematical concepts and implementation principles behind spectral modularity, eigenvalue-based community detection, recursive bisection, and related computational procedures.

AI was used as a supplementary learning resource to improve my understanding of these concepts while working through the assignment.

## 11. References

1. Newman, M. E. J. (2006). **Modularity and community structure in networks.** *Proceedings of the National Academy of Sciences*, 103(23), 8577–8582.

2. DSC212: Graph Theory Module. *Research Assignment – Modularity on the Karate Club Graph*. IISER Thiruvananthapuram.

---

**Course Assignment:** DSC212 – Graph Theory
**Submitted by:** Divyansh Trivedi | **Roll Number:** IMS25073

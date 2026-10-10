# Benchmark Instances for the Fixed Cardinality Binary Quadratic Program

This repository contains instances used in the paper 

*A Parallel Heuristic for the Fixed Cardinality Binary Quadratic Program* by Thi Thanh Tu Le and Thorsten Koch.

The fixed cardinality binary quadratic program (FCBQP):

```math
\begin{aligned}
\min \; / \; \max \quad & f(x) = x^\top Qx \\
\text{s.t.} \quad
& \sum_{i=1}^{n} x_i = k, \\
& x \in \{0,1\}^n,
\end{aligned}
```

where $Q = (q_{ij})_{1 \leq i,j \leq n} \in \mathbb{R}^{n \times n}$ is a cost matrix and $k$ is the required number of selected variables.

Without loss of generality, we can assume that $Q$ is symmetric and  $k \leq n/2$.

- Benchmark instances are stored in the folder `dataset`.
- Best-known or reference objective values are stored in `best_known_results.csv`.
- Links and references identifying the sources of the instances and best-known values are listed in `Related_link.pdf`.

## Overview of Instances

The collection includes instances from three problem classes.

### Maximum Dispersion Problem (MDP)

- Well-known [MDPLIB 2.0](https://www.uv.es/rmarti/paper/mdp.html) benchmark instances.
- Instances used in the paper *A Breakpoints Based Method for the Maximum Diversity and Dispersion Problems* by Dorit S. Hochbaum et al. (2023).

### Maximum Clique Problem (MCP)

- Instances from the [DIMACS](https://archive.dimacs.rutgers.edu/pub/challenge/graph/benchmarks/volume/Clique/) benchmark dataset.
- Instances from the Prof. Ke Xu's Homepage about [BHOSLIB](https://rb-bench.github.io/benchmarks/hidden-opt-graph.html) benchmark dataset.
- Instances used in the paper *On Solving the Densest k-Subgraph Problem on Large Graphs* by Renata Sotirov (2020).

### Graph Bisection Problem (GBP)

- Selected graph-partitioning instances from the [Walshaw Graph Partitioning Archive](https://chriswalshaw.co.uk/partition/).

## Data File Formats

Instance files may use either of the following:

- Zero-based indexing: Variable indices range from `0` to `n - 1`.
- One-based indexing: Variable indices range from `1` to `n`.

### 1. QSC Format

- First line: `k`
- Second line: `n m`
- Each remaining line: `i j q(ij)`

where:

- `k` is the number of selected variables;
- `n` is the number of variables;
- `m` is the number of matrix entries explicitly stored in the file;
- `i` and `j` are variable indices; 
- `q(ij)` is the matrix coefficient $q_{ij}$ associated with the pair $(i, j)$ in the cost matrix $Q$.

Exactly $m$ entry lines follow the second line. Coefficients can be positive or negative, and can be integer- or real-valued. Diagonal entries may be included. All cost matrices are assumed to be symmetric, and entries not listed in the file are treated as zero.

### 2. TXT Format

- First line: `n k`
- Each remaining line: `i j q(ij)`

where:

- `n` is the number of variables;
- `k` is the number of selected variables;
- `i` and `j` are variable indices;
- `q(ij)` is the matrix coefficient $q_{ij}$ associated with the pair $(i, j)$ in the cost matrix $Q$.

The remaining lines contain the explicitly stored matrix entries. 

## Related Repository

- [A Parallel Heuristic for the FCBQP](https://github.com/LeThiThanhTu/FCBQP_parallel)

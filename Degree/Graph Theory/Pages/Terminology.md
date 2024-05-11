---
tags:
  - incomplete
---
![[Graph Theory MOC 🌍]]
Simple Undirected Graph - Edges have no direction.
Simple Directed Graph - Edges have a direction of travel.
Edge Weighted Graph - Edges have weights.

Independent Set - A set of vertices in which there is no edge between any two.
Maximum Independent Set - Largest independent set.
Minimum colouring - Partition the graph into the smallest number of independent sets.

Dominating Set - A set of vertices such that every vertex is either in the set or adjacent to  a node in the set.
Minimum Dominating Set - The smallest dominating set.

The neighbourhood of a vertex is all the vertices that are adjacent to the vertex.

The degree of a vertex is the number of neighbours that vertex has.
$\delta$ denotes the smallest degree in $G$ and $\Delta$ we denote the largest degree.
A vertex of degree 0 is isolated.
A vertex with degree 1 is an end or pendant vertex.

A subgraph $G' = (V',E')$ of $G(V,E)$ is a graph with $V' \subseteq V$ and $E' \subseteq E$.
A subgraph is proper if the subgraph doesn't match the original, $G' \ne G$.
It's called spanning if it has the same vertices, $V' = V$.
A graph is not a subgraph if it introduces new vertices or edges.

It's called induced subgraph if $E' = E$ for all edges of the vertices in $V'$.
aka, it doesn't remove any edges between nodes that still remain.

A path is a graph $P_{n}$ that is $n$ vertices long with the vertex set $V=\{ v_{1}, v_{2}, v_{n} \}$ and edge set $E = \{ v_{1} v_{2}, v_{2}, v_{3}, \ldots, v_{n-1} v_{n} \}$.
So basically it's a graph that forms a line of $n$ vertices.
Graph $P_{n}$ has $n-1$ edges.

A cycle is a graph $C_{n}$ which is similar to $P_{n}$ but the ends are connected $\{ v_{n} v_{1} \}$.
The edges form a loop.
A graph $C_{n}$ has $n$ edges.




---
### Additional Information

- [Wikipedia]
- [Lecture Notes]
- [Maybe Practical Q and As]

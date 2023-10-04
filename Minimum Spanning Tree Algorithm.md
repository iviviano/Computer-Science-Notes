---
mathLink: minimum spanning tree algorithm
---

Input: 
- [[Connected]] undirected [[Graph]] $G=V,E$
- [[edge]] weights: $w(e)$

Output:
- [[Minimum Spanning Tree]]: [[Spanning Tree]] $(V,T)$ such that $\sum_{e\in T}w(e)$

Ideas:
- Sort the edges by weight. Add the smallest edge that doesn't create a cycle
- Perform a breadth first search from some vertex by exploring across the cheapest edge from any given vertex first
- Remove the heaviest edge that can be removed without disconnecting the graph

>[!alg]
[[Reverse Delete Algorithm]]: look at highest weight edge. If it can be removed without disconnecting the graph, remove it.

>[!alg]
[[Prim's Algorithm]]: pick the cheapest edge out of the current connected component

>[!alg]
>[[Kruskal's Algorithm]]: add the cheapest edge that doesn't create a cycle
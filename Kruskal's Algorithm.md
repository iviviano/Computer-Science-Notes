---
mathLink: Kruskal's algorithm
---
>[!def]
>A [[Greedy Paradigm]] [[Algorithm]] for finding a [[Minimum Spanning Tree]].

>[!alg]
>$$\begin{align}
&\textbf{Algorithm } \text{Kruskal's Algorithm }\\
&\textbf{Input: } \text{Graph } (V,E)\\
&\textbf{Output: } \text{Edge set } T\\
&\text{Sort } E \text{ by weight}\\
&\text{Let } T=\emptyset\\
&\textbf{For } e\in E \textbf{ do:} \\
&\quad \textbf{If } \text{adding } e \text{ to } T \text{ doesn't create cycle }\textbf{ then:} \\
&\quad \quad \ \text{add } e \text{ to } T\\
&\textbf{return } T\\
\end{align}$$


Proof of feasibility: (Show that $T$ is a [[Spanning Tree]])
1. [[Acyclic]]: we never add an [[edge]] if it creates a [[Cycle]], so $T$ must be [[Acyclic]]
2. [[Spanning Tree]]: Assume that $T$ is not [[Connected]]. Then there are two components $T_{1},T_{2}$ with no [[edge]]s connecting them. As $G$ is [[Connected]], there must be some [[edge]] between a [[node]] $v_{1}\in T_{1}$ and a [[node]] $v_{2}\in T_{2}$. Adding the [[edge]] $\{v_{1},v_{2}\}$ does not create a [[Cycle]] as there is no other [[Path]] from $v_{1}$ to $v_{2}$. [[therefore]] our algorithm would have added $\{v_{1},v_{2}\}$.

Proof of Optimality:

Let $S$ be another [[Spanning Tree]] and let $T$ be our solution. Let $\{e_{1},\ldots,e_{n-1}\}=T,\{s_{1},\ldots,s_{n-1}\}=S$ be in [[Sort]]ed order.

Claim: $e_{i}≤s_{i}$.

Base case: Clearly, $e_{1}≤s_{1}$, since a [[Graph]] of $1$ [[edge]] must be [[Acyclic]], and we add the cheapest [[edge]] that doesn't create a [[Cycle]] at every step.

Inductive Step: Assume that for some $i≥1$, for all $1≤i<n-1$, $e_{i}≤s_{i}$.

Suppose that $e_{i+1}>s_{i+1}$.
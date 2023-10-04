---
mathLink: Kruskal's algorithm
---
>[!def]
>A [[Greedy Paradigm]] [[Algorithm]] for finding a [[Minimum Spanning Tree]].

>[!alg]
>1. Sort $E$ by weight.
>2. Let $T=\emptyset$.
>3. For each [[edge]] $e\in E$, if $e$ doesn't create a [[Cycle]] in $T$, add $e$ to $T$.
>4. Return $T$.
>$$\begin{align}
&\textbf{Algorithm } \text{Kruskal's Algorithm }\\
&\textbf{Input: } \text{Graph } (V,E)\\
&\textbf{Output: } \text{Edge set } T\\
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
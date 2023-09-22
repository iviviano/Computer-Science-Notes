---
mathLink: interval scheduling
---

Time Constraints: 
- tasks have start/end times
- one task runs at a time
- too many tasks to run
---

Goal: Schedule as many tasks as possible

---
Formal Problem Statement:
- Input: $n$ jobs
	- job $i$ has start $S_{i}$ and finish $F_{i}$
	- job $i$ runs in interval $[S_{i},F_{i}]$
- Two jobs *conflict* if there run intervals [[Intersects]]
- Output: a [[Set]] of jobs $S$ such that
	- no jobs in $S$ conflict
	- $S$ is as large as possible
---
Naive Algorithm:
1. Compute all possible output sets $S$
2. Return the largest $S$
---
[[Greedy Paradigm]] solution:
1. Choose a dimension of input 
2. Repeatedly add compatible tasks minimizing that input
How to minimize?
1. Pick earliest finish time

>[!alg]
>$$\begin{align}
&\text{Let }S=\emptyset\\
&\text{Sort jobs by finish time } (O(n\log n))\\
&\textbf{For } j\in J \textbf{ do:} \\
&\quad \textbf{If } j \text{ is compatible with } S\textbf{ then:}\text{ }O(n) \\
&\quad \quad \text{Append }j \text{ to } S\\
\end{align}$$

---
Correctness. Must show
- Feasibility (returns compatible schedule)
- Optimality (returns largest set)

>[!proof] Proof of Optimality

Let $ALG$ be our solution and let $ALT$ be any other solution. 
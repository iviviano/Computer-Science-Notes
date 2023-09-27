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

Let $ALG$ be our solution and let $ALT$ be any other solution. We will show $$|ALG|≥|ALT|$$Let $ALG=\{a_{1},\ldots,a_{n}\}$ be [[Sort]]ed by finish time. Let $ALT=\{b_{1},\ldots,b_{k}\}$. Claim: for all $k:f_{a_{i}}<f_{b_{i}}$. We will prove this claim by induction on $i$.

Base case: clearly $f_{a_{1}}≤f_{b_{1}}$ as this was our criteria for selecting the first job.

Inductive Step: assume that for some $i≥1$, $f_{a_{i}}≤f_{b_{i}}$. Suppose that $f_{a_{i+1}}>f_{b_{i+1}}$. Then, $b_{i+1}$ starts after $a_{i}$ so it is compatible with $a_{i}$. As it ends earlier than $a_{i+1}$, we would have chosen $b_{i+1}$ over $a_{i+1}$, so $f_{a_{i+1}}≤f_{b_{i+1}}$.

So, [[Principle of Mathematical Induction]] [[implies]] claim 1 is true.
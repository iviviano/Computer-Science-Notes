---
mathLink: merge sort
---
>[!def]
>A [[Divide and Conquer Paradigm]] [[Sort]]ing [[Algorithm]] that splits the [[List]] into two unsorted lists, [[Sort]]s them [[Recursive]]ly, then merges the now [[Sort]]ed [[List]]s to sort the original list.

>[!alg]
>$$\begin{align}
&\textbf{Algorithm } \text{Merge Sort} \\
&\textbf{Input: } \text{Array } A \\
&\textbf{Output: } \text{Sorted array} A \\
&\textbf{If } \text{len } A == 1 \textbf{ then:} \\
&\quad \textbf{return } \text{} A \\
&\textbf{end if} \\
&\text{Let }U=A[0:\text{len }A/2]\\
&\text{Let }V=A\frac{\text{len }A}{2:\text{len }A}\\
&U=mergesort(U)\\
&V=mergesort(V)\\
&\textbf{return } merge(U,V) \\
& \\
&merge(A,B): \\
&\quad \text{Let } s \text{ be a list} \\
&\quad \textbf{While } A\cup B≠\emptyset \textbf{ do:} \\
&\quad \quad \text{Let } C = \text{ list with smallest first element} \\
&\quad \quad \text{Append } C[0] \text{ to } S \\
&\quad \quad \text{Remove } C[0] \text{ from } C \\
&\quad \textbf{end while} \\
\end{align}$$

>[!proof]

Let $P(n)$ be merge sort [[Sort]]s an input of size $n$ for $n\in \mathbb{N}$.

Base case: $n=1$.
A singleton is [[Sort]]ed, so $P(1)$.

Inductive step: Assume $P(n)$ for all $k≥n≥1$ for some $k\in \mathbb{N}$.
Then 
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
&\quad \textbf{return } s \\
\end{align}$$

>[!proof]
Let $P(n)$ be merge sort [[Sort]]s an input of size $n$ for $n\in \mathbb{N}$.
>
Base case: $n=1$.
A singleton is [[Sort]]ed, so $P(1)$.
>
Inductive step: Assume $P(n)$ for all $k≥n≥1$ for some $k\in \mathbb{N}$.
Then given a [[List]] of size $k+1$, split this into two lists $A,B$ where $A$ contains the first $\left\lfloor\frac{k+1}{2}\right\rfloor$ elements of the input and $B$ contains the rest. As $\left\lceil \frac{k+1}{2}\right\rceil≤k$, merge sort works for $A$ and $B$. If $merge$ combines $A$ and $B$ in sorted order, then the input list of size $k+1$ is sorted, so $P(k+1)$.
>
[[therefore]] By [[Principle of Mathematical Induction]], $P(n)$ for all $n\in \mathbb{N}$

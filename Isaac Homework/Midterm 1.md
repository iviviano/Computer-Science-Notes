>[!note] 1

(a) Repeat the following until $S$ has $k$ elements put the largest element of $A$ in $S$; remove one instance of this element from $A$. 

As $A$ is finite, it has a largest element. Clearly, this is a feasible algorithm as each element of $S$ comes from $A$ and $k$ elements of $A$ are added to $S$.

>[!proof]
Let $S$ be the solution given by our [[Greedy Paradigm]] [[Algorithm]] and let $X$ be any other [[Subset]] of $A$ with $k$ elements. Sort both $S$ and $X$ by non-increasing order of elements.
>
Suppose that $k>0$. Clearly, if $k=0$, $S=X=\emptyset$, so $S$ is optimal.
>
Let $P(i)$ be the statement that $S[i]≥X[i]$.
>
Base Case: $i=1$. 
As $S$ is sorted in non-increasing order and $S$ contains the largest element of $A$, $S[1]$ is the largest element of $A$. As $X$ is also a [[Subset]] of $A$, $X[1]$ is not larger than the largest element of $A$. So, $S[1]≥X[1]$, giving $P(1)$.
>
Inductive Step: let $i\in[k-1]$ and suppose that $P(i)$ is true.
$S[i]$ was the largest element of $A$ before it was removed, and $X[i]≤S[i]$. $X[i+1]≤X[i]$ as $X$ is in non-increasing order. So, $X[i+1]≤S[i]$. As there are $i$ elements of $X$ at least as large as $X[i+1]$, there are at least $i$ elements of $A$ at least as large as $X[i+1]$. So, $X[i+1]$ was still in $A$ when $S[i+1]$ was chosen. As $S[i+1]$ was the largest element of $A$ at this point, $X[i+1]≤S[i+1]$. $\therefore P(i+1)$.
>
Therefore, by [[Principle of Mathematical Induction]], $P(i)$ for all $i\in[k]$.
>
As $S[i]≥X[i]$ for all $1≤i≤k$, clearly $$\sum_{i=1}^{k}S[i]≥\sum_{i=1}^{k}X[i]$$So, no possible solution is better than $S$, showing that my [[Algorithm]] is optimal.

(b) False. For [[mer]]
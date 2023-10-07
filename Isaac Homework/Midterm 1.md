>[!note] 1

(a) Repeat the following until $S$ has $k$ elements put the largest element of $A$ in $S$; remove this element from $A$. 

As $A$ is finite, it has a largest element. Clearly, this is a feasible algorithm as each element of $S$ comes from $A$ and $k$ elements of $A$ are added to $S$.

>[!proof]
Let $S$ be the solution given by our [[Greedy Paradigm]] [[Algorithm]] and let $X$ be any other [[Subset]] of $A$ with $k$ elements. Sort both $S$ and $X$ by non-increasing order of elements.

Suppose that $k>0$. Clearly, if $k=0$, $S=X=\emptyset$, so $S$ is optimal.

Let $P(i)$ be the statement that $\sum_{j=1}^{i}S[j]≥\sum_{j=1}^{i}X[j]$.

Base Case: $i=1$. 
$\sum_{j=1}^{1}S[j]=S[1]$, and $\sum_{j=1}^{1}X[j]=X[j]$. As $S$ is sorted in non-increasing order and $S$ contains the largest element of $A$, $S[1]$ is the largest element of $A$.
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

(b) False. Let $T(n)=n^{3}\log_{2}n$. Then, $$T\left(\frac{n}{2}\right)=\frac{n^{3}}{8}\log_{2}\frac{n}{2}$$so, $$\begin{align*}\\
8T\left(\frac{n}{2}\right)+n^{3}&=8 \frac{n^{3}}{8}\log_{2} \frac{n}{2}+n^{3}=n^{3}\log_{2}n -n^{3}\log_{2}2+n^{3}\\\\
&= n^{3}\log_{2}n-n^{3}+n^{3}=n^{3}\log_{2}n=T(n)
\end{align*}$$so, $T(n)$ satisfies the recurrence relation. However, $T(n)=O(n^{3}\log n)$, so $T(n)≠O(\log n)$.

(c) 
>[!proof]
Let $P(n)$ be that $T(n)=\frac{n}{2}+1$.
>
Base Case: $n=0$.
If $n=0$, $\frac{n}{2}+1=\frac{0}{2}+1=1=T(0)$. So, $T(0)$. 
>
Inductive Step: let $n>0$ be even, and assume $P(n-2)$. 
$$T(n)=T(n-2)+1=\frac{n-2}{2}+1+1=\frac{n}{2}-1+2=\frac{n}{2}+1$$So, $P(n)$.
>
By (PMI), $P(n)$ for all even $n≥0$.

So, $T(n)=O(n)$ by the [[Asymptotic Tight Bound for Polynomials Proposition]].

(d) True. Clearly, this does not increase the cost of $T$. As there were already no other [[Spanning Tree]]s with lower cost than $T$, $T$ is still a [[Minimum Spanning Tree]].

(e) To prove that this is feasible, we must show that its output is a [[Spanning Tree]]. A [[Spanning Tree]] $T$ is a [[Subset]] of $E$ such that $(V,T)$ is [[Connected]] and [[Acyclic]]. Clearly, $T$ is a [[Subset]] of $E$, as it starts as all of $E$ and elements are removed from there. It is also obvious that $E$ is connected, since we assume that $G$ is connected, and no edges are removed from $T$ that disconnect it.

If $T$ had a [[Cycle]], then some edge could be removed without disconnecting $(V,T)$. So, the [[Algorithm]] cannot end without $T$ being acyclic. As there are finitely many edges the algorithm does terminate. [[therefore]] $T$ is a [[Spanning Tree]]


>[!note] 2

(a)
>[!alg]

$$\begin{align*}
&\textbf{Algorithm } \text{Double Index Element?}\\\\
&\textbf{Input: } \text{Sorted Array } A \text{ of length }n \text{ with no duplicate elements}\\\\
&\textbf{Output: } \text{Boolean indicating whether }A[i]=2i \text{ for some }i\in[n]\\
&\textbf{return } fun(0,n)\\
&\\
&fun(start,end):\\
&\quad \text{Let }l=end-start\\
&\quad \text{Let }middle=\left\lfloor\frac{l}{2}\right\rfloor+start\\
&\quad \text{Let }found=\text{false}\\
&\quad \textbf{If } n\%2=1 \textbf{ then:}\\
&\quad \quad found=A[middle]==2middle\\\\
&\quad \textbf{If } found\lor l==1 \textbf{ then:}\\
&\quad \quad \textbf{return } found\\
&\quad \textbf{If } A[middle]>2middle \textbf{ then:}\\
&\quad \quad \textbf{return } fun(start,middle)\\
&\quad \textbf{Else:}\\
&\quad \quad \textbf{return } fun\left(\left\lceil \frac{l}{2}\right\rceil+start,end\right)
\end{align*}$$

Let $P(l)$ be that if $end-start=l$ $fun(start,end)$ returns $\text{true}$ if $\exists i:start≤i<end:A[i]=2i$ and $\text{false}$ otherwise.

Base Case: $l=1$
$\lfloor \frac{l}{2}\rfloor=\lfloor \frac{1}{2}\rfloor=0$, so $middle$ is assigned to $start$. Since $n\%2=1\%2=1$, $found$ is assigned to whether $A[start]=2start$. Since $l==1$, $found$ is returned. As $start$ is the only integer at least as big as $start$ and less than $end$ in this case $found$ is $\text{true}\iff\exists i:start≤i<end$. $\therefore P(1)$ holds.

Inductive Step: let $l$ be given with $1<l≤n$ and assume that for all $k\in[k-1],P(k)$.
Suppose that $l$ is even. Then, $\lfloor \frac{l}{2}\rfloor=\lceil \frac{l}{2}\rceil= \frac{l}{2}$. $found$ is $\text{false}$, and $l>1$, so we reach the final $\textbf{If}$ statement. Suppose that $A[middle]>2middle$. Then, for each $i:middle≤i<end:A[i]$

Otherwise $l$ is odd.

Runtime Analysis:
The [[Worst Case Run Time]] for this [[Algorithm]] occurs when 


(b) $A=$
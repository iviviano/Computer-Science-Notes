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
&\quad \textbf{If } A[middle]\ge 2end-l \textbf{ then:}\\
&\quad \quad \textbf{return } fun(start,middle)\\
&\quad \textbf{If } A[middle]\le2start+l \textbf{ then:}
&\quad \textbf{Else:}\\
&\quad \quad \textbf{return } fun\left(\left\lceil \frac{l}{2}\right\rceil+start,end\right)
\end{align*}$$

Let $P(l)$ be that if $end-start=l$ $fun(start,end)$ returns $\text{true}$ if $\exists i:start≤i<end:A[i]=2i$ and $\text{false}$ otherwise.

Base Case: $l=1$
$\lfloor \frac{l}{2}\rfloor=\lfloor \frac{1}{2}\rfloor=0$, so $middle$ is assigned to $start$. Since $n\%2=1\%2=1$, $found$ is assigned to whether $A[start]=2start$. Since $l==1$, $found$ is returned. As $start$ is the only integer at least as big as $start$ and less than $end$ in this case $found$ is $\text{true}\iff\exists i:start≤i<end$. $\therefore P(1)$ holds.

Inductive Step: let $l$ be given with $1<l≤n$ and assume that for all $k\in[k-1],P(k)$.
Suppose that $l$ is even. Then, $\lfloor \frac{l}{2}\rfloor=\lceil \frac{l}{2}\rceil= \frac{l}{2}$. $found$ is $\text{false}$, and $l>1$, so we reach the final $\textbf{If}$ statement. Suppose that $A[middle]\ge2middle$. Then, for each $i:middle≤i<end:A[i]$

Otherwise $l$ is odd.

Runtime Analysis:
The [[Worst Case Run Time]] for this [[Algorithm]] occurs when 


(b) 


>[!note] 3
(a) Let $P=\{1,4\},W=\{3,6\}$. The [[Algorithm]] by smallest $|p_{i}-w_{f(i)}|$ will make associations: $(1,6),(4,3)$ of pumpkin-watermelon pairs. The average difference for this solution is $$\sum_{i=1}^{2}|p_{i}-w_{f(i)}|=|1-6|+|4-3|=5+1=6$$If instead, we used the associations $(1,3),(4,6)$, the average difference would be $$\sum_{i=1}^{2}|p_{i}-w_{f(i)}|=|1-3|+|4-6|=2+2=4$$

(b) 
For this proof, I will use the [[Triangle Inequality]]: $$\begin{equation}
|A-B|≤|A|+|B|
\end{equation}$$

[[Exchange Argument]]:
Let $f$ be a matching of pumpkins to watermelons where the pumpkins are sorted by non-decreasing weight.
Let $i\in[n-1]$ be given with $w_{f(i)}≥w_{f(i+1)}$. Let $g:[n]\rightarrow[n]$ be defined by$$g(j)=\left\{\begin{align}
&f(j+1)\text{ if }j=i\\
&f(j-1)\text{ if }j=i+1\\
&f(j)\text{ otherwise}\\
\end{align}\right.$$Clearly, $g$ is a valid matching function, as $f$ is. I will show that $$\frac{1}{n}\sum_{j=1}^{n}|p_{j}-w_{g(j)}|\le \frac{1}{n}\sum_{j=1}^{n}|p_{j}-w_{f(j)}|$$The only two different terms in this sum are for $j=i,i+1$, since these are the only two inputs for which $f$ and $g$ differ. So, I must only show $$|p_{i}-w_{g(i)}|+|p_{i+1}-w_{g(i+1)}|≤|p_{i}-w_{f(i)}|+|p_{i+1}-w_{f(i+1)}|$$
Now, $$\begin{align*}\\
&|p_{i}-w_{g(i)}|+|p_{i+1}-w_{g(i+1)}|=|p_{i}-w_{f(i+1)}|+|p_{i+1}-w_{f(i)}|\\
\end{align*}$$
There are 3 cases that must be considered:

Case $1$: $p_{i}≤w_{f(i+1)},p_{i+1}\le w_{f(i)}$. Then, $$|p_{i}-w_{f(i+1)}|+|p_{i+1}-w_{f(i)}|=w_{f(i+1)}-p_{i}+w_{f(i)}-p_{i+1}$$
Now, $$\begin{align*}
&w_{f(i+1)}-p_{i}+w_{f(i)}-p_{i+1}\le |w_{f(i+1)}-p_{i}+w_{f(i)}-p_{i+1}|\\
&=|w_{f(i)}-p_{i}+w_{f(i+1)}-p_{i+1}|\le|w_{f(i)}-p_{i}|+|w_{f(i+1)}-p_{i+1}| \quad(1)\\
&=|p_{i}-w_{f(i)}|+|p_{i+1}-w_{f(i+1)}|
\end{align*}$$
Case 2: $p_{i}\le w_{f(i+1)},p_{i+1}>w_{f(i)}$. Then, $$|p_{i}-w_{f(i+1)}|+|p_{i+1}-w_{f(i)}|=w_{f(i+1)}-p_{i}+p_{i+1}-w_{f(i)}$$
Apply $w_{f(i)}≥w_{f(i+1)}$: $$\begin{align*}\\
&w_{f(i+1)}-p_{i}+p_{i+1}-w_{f(i)}≤w_{f(i)}-p_{i}+p_{i+1}-w_{f(i+1)}\\
&\le|w_{f(i)}-p_{i}+p_{i+1}-w_{f(i+1)}|\le|w_{f(i)}-p_{i}|+|p_{i+1}-w_{f(i+1)}|\quad(1)\\
&=|p_{i}-w_{f(i)}|+|p_{i+1}-w_{f(i+1)}|
\end{align*}$$
Case 3: $p_{i}>w_{f(i+1)},p_{i+1}>w_{f(i)}$. Then, $$|p_{i}-w_{f(i+1)}|+|p_{i+1}-w_{f(i)}|=p_{i}-w_{f(i+1)}+p_{i+1}-w_{f(i)}$$
Now, $$\begin{align*}
&p_{i}-w_{f(i+1)}+p_{i+1}-w_{f(i)}\le|p_{i}-w_{f(i+1)}+p_{i+1}-w_{f(i)}|\\
&=|p_{i}-w_{f(i)}+p_{i+1}-w_{f(i+1)}|≤|p_{i}-w_{f(i)}|+|p_{i+1}-w_{f(i+1)}|\quad(1)\\
\end{align*}$$
The last possible combination: $p_{i}>w_{f(i+1)},p_{i+1}\le w_{f(i)}$ is not actually possible: $$w_{f(i+1)}<p_{i}≤p_{i+1}$$as $p$ is non-increasing. So, this condition implies that $w_{f(i+1)}<w_{f(i)}$, contradiction my assumption otherwise.

So, for all possible values of $p_{i},p_{i+1},w_{f(i)},w_{f(i+1)}$ with the stipulation $w_{f(i)}\ge w_{f(i+1)}$, $$\frac{1}{n}\sum_{j=1}^{n}|p_{j}-w_{g(j)}|\le \frac{1}{n}\sum_{j=1}^{n}|p_{j}-w_{f(j)}|$$This proves that the swap of any two "adjacent" watermelons $w_{f(i)},w_{f(i+1)}$ doesn't worsen the solution. 

Let $f$ be any matching of pumpkins to watermelons with the watermelons. Sort the watermelons in non-decreasing order. Then, $f$ induces an ordering of the pumpkins. Sort this ordering in non-decreasing order with bubble sort. (CLARIFY). 



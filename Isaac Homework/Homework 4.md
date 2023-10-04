
>[!note] 1
(a) Here is a counterexample for $n=3$. Let $w=(3,2,1),h=(1,2,1)$. The given [[Greedy Paradigm]] [[Algorithm]] will pick rectangle $1$, the widest, and then finish as neither of the others nests inside. The correct solution is to pick rectangle $2$ first as this allows $3$ to nest inside.
![[IMG-1263.jpg]]
>
(b) Here is a counterexample for $n=3$. Let $w=(4,2,1),h=(1,2,1)$, so $p=(10,8,4)$. The given [[Greedy Paradigm]] [[Algorithm]] will pick rectangle $1$, the largest perimeter, and then finish as neither of the others nests inside. The correct solution is to pick rectangle $2$ first as this allows $3$ to rest inside. 
![[IMG-1264.jpg]]
>
(c) Here is a counterexample for $n=3$. Let $w=(5,2,1),h=(1,2,1)$, so $a=(5,4,1)$. The given [[Greedy Paradigm]] [[Algorithm]] will pick rectangle $1$, the largest area, and then finish as neither of the others nests inside. The correct solution is to pick rectangle $2$ first as this allows $3$ to nest inside.
![[IMG-1265.jpg]]
>
(d) Here is a counterexample for $n=3$. Let $w=(4,3,1),h=(2,1,2)$, so $a=(8,3,2)$. The given [[Greedy Paradigm]] [[Algorithm]] will pick rectangle $3$, the smallest area, and then finish as it cannot nest in either of the others. The correct solution is to pick rectangle $1$ first as this allows $2$ to nest inside.
![[IMG-1266.jpg]]

>[!note] 2
Note: this problem uses $1$-indexing.
>
(a) $g[1]=2,g[2]=7,g[3]=9,g[3]=10$
>
(b)
>>[!proof]
Suppose that the algorithm returns true. I will show that $g$ gives an increasing function from $[n]$ to $[m]$. 
>>
Clearly, $g[j]<g[j+1]$ for all $j\in[m-1]$. No index of $g$ can be $\infty$, as the algorithm only returns true if the last index of $g$ is finite and indices of $g$ are reassigned sequentially. $i$ is monotonic as it is incremented each iteration of the loop. As each index of $g$ is assigned to a value of $i$, and at most one index of $g$ is assigned per iteration of the loop, the indices of $g$ must be monotonic increasing.
>>
Also, $t_{j}=w_{g[j]}$ as $g[j]$ is assigned to $i$ only if $t_{j}=w_{i}$, and each index of $g$ was assigned to a value of $i$ since the algorithm returned true.
>>
[[therefore]] $f:[m]\rightarrow [n]$ given by the [[Rule of Assignment]] $f(j)=g[j]$ is a monotonic increasing function with $t_{j}=w_{g[j]}$. So, $T$ is a valid secret message.
>
(c) 
>>[!proof]
>Claim: If $f:[m]\rightarrow[n]$ is an increasing map with $t_{j}=w_f(j)$ for all $j\in[m]$, then $g[j]≤f(j)$ for $j\in[m]$. 
>>
Base case: $j=1$.
$g[1]$ is assigned to $i$ if $w_{i}=t_{1}$. By the definition of $f$, this is the value of $i$ that equals $f(1)$. So, $g[1]≤f(1)$.
>>
Inductive Step: Suppose that for some $j\in[m-1]$, $g[j]≤f(j)$.
Suppose that $g[j+1]>f(j+1)$. Then, if $g[j]<i≤f(j+1)$, $t_{j+1}≠w_{i}$. In particular, if $i=f(j+1)$, $t_{j+1}≠w_{i}$. But this contradicts our that $t_{j+1}=w_{f(j+1)}$. So, $g[j+1]≤f(j+1)$.
>>
[[therefore]] by [[Principle of Mathematical Induction]], $g[j]≤f(j)$ for all $j\in[m]$.
>
(d) Suppose that $T$ is a valid secret message. Pick an increasing function $f:[m]\rightarrow[n]$ such that $t_{j}=w_{f(j)}$ for all $j\in[m]$. Then, for all $j\in[m]$, $g[j]≤f(j)$ by (c). In particular, $g[m]≤f(m)≤n<\infty$, so the algorithm will return true.


>[!note] 3
Sort the $n$ requests by smallest $\frac{t_{i}}{v_{i}}$. This is the ordering of requests to return.
>
Clearly, this algorithm has [[Worst Case Run Time]] $O(n\log n)$, as this is the cost of sorting the requests.
>
[[Exchange Argument]]:
>
Let there be an order of $n$ requests and let $i<n$ be given with $\frac{t_{i}}{v_{i}} > \frac{t_{i+1}}{v_{i+1}}$. Swapping requests $i$ and $i+1$ only affects the terms $i,i+1$ of the sum, as both $T_{j}$ and $v_{j}$ are unchanged for $j<i$ or $j>i+1$. I will show that $$\begin{align}(T_{i-1} +t_{i+1})v_{i+1}+(T_{i-1}+t_{i+1}+t_{i})v_{i}<\\(strict?)(T_{i-1}+t_{i})v_{i}+&(T_{i-1}+t_{i}+t_{i+1})v_{i+1}\end{align}$$
that is the sum of the $i$ and $i+1$ terms after the swap is not worse than the sum of the $i$ and $i+1$ terms before. As these are the only terms of the sum changed by the swap, this will show that the swap does not make the solution less optimal.
>
>$$\begin{align}
(T_{i-1}+t_{i+1})v_{i+1}+(T_{i-1}+t_{i+1}+t_{i})v_{i}& \\
-\text{    }(T_{i-1}+t_{i})v_{i}+(T_{i-1}+t_{i}+t_{i+1})v_{i+1}&\\
\hline \\
T_{i-1}v_{i+1}+t_{i+1}v_{i+1}+T_{i-1}v_{i}+t_{i+1}v_{i}+t_{i}v_{i}-T_{i-1}v_{i}-t_{i}v_{i}-T_{i-1}v_{i} -t_{i}v_{i+1}-t_{i+1}v_{i+1}& \\
=t_{i+1}v_{i}-t_{i}v_{i+1}
\end{align}$$
Since $t_{i}v_{i+1}>t_{i+1}v_{i}$, $t_{i+1}v_{i}-t_{i}v_{i+1}<0$, so $$\begin{align}(T_{i-1} +t_{i+1})v_{i+1}+(T_{i-1}+t_{i+1}+t_{i})v_{i}<\\(strict?)(T_{i-1}+t_{i})v_{i}+&(T_{i-1}+t_{i}+t_{i+1})v_{i+1}\end{align}$$holds.
>
Now, let any alternative solution, $S$, be given. Sort $S$ based on smallest $\frac{t_{i}}{v_{i}}$ with [[Bubble Sort]]. Clearly, this gives my solution. Additionally, since each change to the list in bubble sort only swaps adjacent elements, the [[Exchange Argument]] shows that my solution is no worse than $S$.
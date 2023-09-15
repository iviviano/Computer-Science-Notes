>[!note] 1

(a) 
1. $f=O(g)$
2. $f=\Omega(g)$
3. $f=\Theta(g)$
4. $f=O(g)$
5. $f=\Theta(g)$
6. $f=\Theta(g)$
7. $f=\Omega(g)$

(b)
1. Each of the subproblems of size $\frac{n}{d}$ requires $T(\frac{n}{d})$ [[Primitive Computational Step]]s by our definition of $T$. As there are $a$ subproblems, the number of [[Primitive Computational Step]]s from subproblems is $aT(\frac{n}{d})$. The steps for merging the solutions to the subproblems must be added to steps from subproblems. [[therefore]] the total [[Worst Case Run Time]] is given by the equation: $$T(n)=aT\left(\frac{n}{d}\right)+O(n^{d}) $$
2. Pick $N\in \mathbb{N}, c\in \mathbb{R}$ such that if $n≥N$, 

Suppose $T(1)=c$.

Inductive Step: Suppose that for all $k\in\{1,\ldots,n\}$, $P(k)$.
Then, $$\begin{align} T(n+1)&=aT\left(\frac{n}{d}\right)+O(n^{d})=a\left(\frac{n}{d}\right)^{d}\log\left(\frac{n}{d}\right)+O(n^{d}) \\ &= \frac{a}{d^{d}}n^{d}\log n-\end{align}$$

>[!note] 2


>[!note] 3



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
Then, $$\begin{align} T(n+1)&=aT\left(\frac{n}{d}\right)+O(n^{d})=a\left(\frac{n}{d}\right)^{d}\log\left(\frac{n}{d}\right)+O(n^{d}) \\ &= \frac{a}{d^{d}}n^{d}\log n- \frac{a}{d^{d}}\log d+O(n^{d})=O(n^{d}\log n)\end{align}$$
(3) 

>[!note] 2

>[!alg]
>$$\begin{align}
&\textbf{Algorithm } \text{Merge Sort} \\
&\textbf{Input: } \text{Array } A \\
&\textbf{Output: } \text{Sorted array} A \\
&\textbf{If } \text{len } A == 1 \textbf{ then:} \\
&\quad \textbf{return } \text{} A \\
&\textbf{end if} \\
&\text{Let } len \text{ be the number of elements in }A\\
&\text{Let }U=A\left[0:\frac{len}{3}\right]\\
&\text{Let }V=A\left[\frac{len}{3}: \frac{2len}{3}\right]\\
&\text{Let }W=A\left[\frac{2len}{3}:len\right]\\
&U=mergesort(U)\\
&V=mergesort(V)\\
&W=mergesort(W)\\
&\textbf{return } merge(U,V,W) \\
& \\
&merge(A,B,C): \\
&\quad \text{Let } S \text{ be a list} \\
&\quad \textbf{While } A\cup B\cup C≠\emptyset \textbf{ do:} \\
&\quad \quad \text{Let } D \in\{A,B,C\} \text{ such that } D[0]=\min\{A[0],B[0],C[0]\} \\
&\quad \quad \text{Append } C[0] \text{ to } S \\
&\quad \quad \text{Remove } C[0] \text{ from } C \\
&\quad \textbf{end while} \\
&\quad \textbf{return } S \\
\end{align}$$

(b) $O(n)$

(c) $T(n)=3T\left(\frac{n}{3}\right)+O(n)$
Split into three subproblems of size $\frac{n}{3}$. Merge the resulting lists with runtime $O(n)$.

(d) $O(n\log n)$

(e) 

>[!note] 3



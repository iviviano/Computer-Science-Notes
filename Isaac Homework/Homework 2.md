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
1. Each of the subproblems of size $\frac{n}{b}$ requires $T(\frac{n}{d})$ [[Primitive Computational Step]]s by our definition of $T$. As there are $a$ subproblems, the number of [[Primitive Computational Step]]s from subproblems is $aT(\frac{n}{b})$. The steps for merging the solutions to the subproblems must be added to steps from subproblems. [[therefore]] the total [[Worst Case Run Time]] is given by the equation: $$T(n)=aT\left(\frac{n}{b}\right)+O(n^{d}) $$
2. Let $P(n)$ be that $T(n)≤an^{d}\log_{b} n$ 

Base Case: $n=b$. 
$$T(b)=aT\left(\frac{b}{b}\right)+O(b^{d})=ac$$

Inductive Step: Let $n\in \mathbb{N}$ with $n>b$. Suppose that $P(k)$ holds for all $b≤k<n$.
$$T(n+1)=a\cdot T\left(\frac{n+1}{b}\right)+O((n+1)^{d})$$by the known recurrence relation. As $\frac{n+1}{b}≤n$, $P(\frac{n+1}{b})$ by the inductive hypothesis. So, (NEEDS SOME WORK) $$T\left(\frac{n+1}{b}\right)≤\left(\frac{n+1}{b}\right)^{d}\log\left(\frac{n+1}{b}\right)+O(n)≤\left(\frac{n+1}{b}\right)^{d}\log(n+1)+O(n)$$By the [[Asymptotic Tight Bound for Polynomials Proposition]], $O((n+1)^{d})=O(n^{d})$. So,  $$T(n+1)≤a\cdot \frac{(n+1)^{d}}{b^{d}}\log(n+1) + O(n)=(n+1)\log(n+1)+O(n)$$So, $P(n+1)$.

[[therefore]] by [[Principle of Mathematical Induction]], ...

3. $T(n)=O(n^{n})$
Most work on the lowest layer.

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
>[!alg]
>$$\begin{align}
&\textbf{Algorithm } k\text{-Merge} \\
&\textbf{Input: } k\text{ sorted lists} \\
&\textbf{Output: } \text{A sorted list containing all the elements of the input lists} \\
&\text{Let } Q \text{ be a priority queue of lists. Use as comparitor the given} \\
&\quad \text{sorting comparitor applied to the first elements of any two lists }\\
&\text{Let } S \text{ be a list }\\
&\text{Add each of the input lists to }Q\\
&\textbf{While } Q≠\emptyset \textbf{ do:} \\
&\quad A = dequeue(Q) \\
&\quad \text{Append }A[0] \text{ to }S\\
&\quad \text{Remove the first element of }A\\
&\quad \textbf{If } A≠\emptyset \textbf{ then:} \\
&\quad \quad \text{Add } A \text{ to } Q\\
&\quad \textbf{end if} \\
&\textbf{end while}
\end{align}$$

(f)
$T(n)=kT(\frac{n}{k})+O(n\log k)$


>[!note] 3


(a) $(l_{1},h_{1}),(r_{1},0)$

(b) 
Naive Solution:
$$\begin{align}
&\text{Let } S \text{ be a list }\\
&\text{Add whichever starting point has smaller } x \text{ to } S\\ 
&\text{Remove the added point from its list}\\
&\textbf{While } S_{1}≠\emptyset\lor S_{2}≠\emptyset \textbf{ do:} \\
&\quad \text{Let } S' \text{ be the list with the smaller first } x \text{ coord}\\
&\quad \textbf{If } S[i]_{y} < S'[0]_{y} \textbf{ then:} \\
&\quad \quad \text{Add }(S'[0]) \text{ to } S\\
&\quad \textbf{end if}\\
&\quad \text{Remove } S'[0]\\
&\textbf{end while}\\
&\text{Append } S_{1} \text{ and }S_{2} \text{ to } S(\text{ one will be empty})\\
\end{align}$$

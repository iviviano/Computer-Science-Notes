>[!note] 1
(a) 
>1. $f=O(g)$
>2. $f=\Omega(g)$
>3. $f=\Theta(g)$
>4. $f=O(g)$
>5. $f=\Theta(g)$
>6. $f=\Theta(g)$
>7. $f=\Omega(g)$

(b)
1. Each of the subproblems of size $\frac{n}{b}$ requires $T(\frac{n}{d})$ [[Primitive Computational Step]]s by our definition of $T$. As there are $a$ subproblems, the number of [[Primitive Computational Step]]s from subproblems is $aT(\frac{n}{b})$. The steps for merging the solutions to the subproblems must be added to steps from subproblems. [[therefore]] the total [[Worst Case Run Time]] is given by the equation: $$T(n)=aT\left(\frac{n}{b}\right)+O(n^{d}) $$
2. 
Rewrite the recurrence relation: $$T(n)≤aT\left(\frac{n}{b}\right)+cn^{d}$$with $c≥T(1)$ fixed.

>[!proof]
Let $P(n)$ be that $T(n)≤cn^{d}\log_{b} n+cn^{d}$. 
>
Induction on $n$:
>
Base Case: $n=b$. 
$$T(b)=aT\left(\frac{b}{b}\right)+cb^{d}≤ac+cb^{d}≤cb^{d}\log_{b}b+cb^{d}$$as $a=b^{d}$. So, $P(b)$.
>
Inductive Step: Let $n\in \mathbb{N}$ with $n>b$. Suppose that $P(k)$ holds for all $b≤k<n$.
>$$T(n)≤aT\left(\frac{n}{b}\right)+cn^{d}≤a\left(c\left(\frac{n}{b}\right)^{d}\log_{b}\left(\frac{n}{b}\right)+c \left(\frac{n}{b}\right)^{d}\right)+cn^{d}$$
By the inductive hypothesis. Note: 
>$$\begin{align}
&T(n)≤a\left(c\left(\frac{n}{b}\right)^{d}\log_{b}n-c\left(\frac{n}{b}\right)^{d}+c \left(\frac{n}{b}\right)^{d}\right)+cn^{d} \\
&≤ \frac{ac}{b^{d}}n^{d}\log_{b}(n)+cn^{d}≤cn^{d}\log_{b}(n)+cn^{d}
\end{align}$$
as $a=b^{d}$. So, $P(n)$.
>
[[therefore]] by [[Principle of Mathematical Induction]], $P(n)$ for all $n$.

If $n_{0}=b$ and $\alpha=2 \frac{c}{\log b}$ , for all $n≥n_{0}$, $$T(n)≤cn^{d}\log_{b}n+cn^{d}=cn^{d}\frac{\log n}{\log b}+cn^{d}≤2 \frac{c}{\log b}\log n=\alpha n\log n$$
[[therefore]] $T=O(n\log n)$.

3. $T(n)=O(n^{n})$
The most work is done on the lowest layer, so this is the only layer that matters for the [[Asymptotic Upper Bounds]]. Formally, $$L(1)≥\alpha\sum_{i=1}^{l}L(i)$$where $l$ is the number of layers ($l\sim\log_{b}n$ CHECK) and $L(i)$ measures the [[Time Complexity]] of layer $i$. So, $T=O(\sum L(i))=O(L(1))$. 

Claim: there are $a^{\log_{b}n}$ subproblems on the first layer. $$a^{\log_{b}n}=a^\frac{\log_{a} n}{\log_{a} b}=(a)$$

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


(c)
>[!alg]
>$$\begin{align}
&\textbf{Algorithm } \text{Merge Two Silhouettes}\\
&\textbf{Input: } \text{Silhouettes } S_{1},S_{2}\\
&\textbf{Output: } \text{The merged silhouette}\\
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
&\text{Append } S_{1} \text{ and }S_{2} \text{ to } S \text{ }(\text{one will be empty})\\
&\textbf{return } S\\
\end{align}$$

>[!alg]
>$$\begin{align}
&\textbf{Algorithm } \text{Skyline}\\
&\textbf{Input: } \text{List } B \text{ of buildings}\\
&\textbf{Output: } \text{List of points constituting the skyline}\\
&\textbf{If } \text{len }B==1 \textbf{ then:} \\
&\quad l=B[0][0]; h=B[0][1]; r=B[0][2]\\
&\quad \textbf{return } \text{List }((l,h),(r,0))\\
&\textbf{end if}\\
&\text{Let }S_{1}=skyline\left(B\left[0:\frac{\text{len }B}{2}\right]\right)\\
&\text{Let }S_{2}=skyline\left(\left[\frac{\text{len }B}{2}:\text{len }B\right]\right)\\
&\textbf{return } merge(S_{1},S_{2})\\
\end{align}$$


>[!proof] Proof of Correctness

Let $P(n)$ be the statement that $skyline$ [[Algorithm]] works for inputs of size $n$.

Base Case: $n=1$.
Converting one building to a silhouette does not change the picture.


Inductive Step: let $n>1$ be given. Assume that $P(k)$ holds for all $1≤k<n$.
By the inductive hypothesis, $S_{1}$ and $S_{2}$ are two skylines that must be merged. I shall prove that $merge$ correctly merges them.


[[therefore]] by [[Principle of Mathematical Induction]], $P(n)$ for all $n\in \mathbb{N}$.


Runtime Analysis


Recurrence Relation: $$T(n)≤2T\left(\frac{n}{2}\right)+dn$$ for $n≥2$ where $d$ is fixed by the definition of an [[Asymptotic Upper Bounds]]. Pick $c\in \mathbb{R}$ such that $T(1)≤c≥d$. The recurrence relation holds, as the merge step only requires iterating through two lists each of size $\frac{n}{2}$. Clearly, merge runs in linear time. The rest of the computational steps come from the two recursive calls with the first and second half of the list of buildings. So, $T$ does satisfy the recurrence.

>[!proof]
Let $P(n)$ be that $T(n)≤cn\log_{2}(n)+dn$.
>
Induction on $n$:
>
Base Case: $n=2$.
By the recurrence relation, $$T(2)=2T(1)+2d=2c+2d≤2c\log_{2}(2)+2d$$so $P(2)$.
> 
Inductive Step: let $n>2$. Assume that $P(k)$ holds for all $2≤k<n$.
$$T(n)≤2T\left(\frac{n}{2}\right)+dn≤2\left(c\frac{n}{2}\log_{2}\left(\frac{n}{2}\right)+ d\frac{n}{2}\right)+dn$$by the inductive hypothesis. 
>$$\begin{align}
&2\left(c \frac{n}{2}\log_{2}\left(\frac{n}{2}\right)+d \frac{n}{2}\right)+dn=2\left(c \frac{n}{2}\log_{2}\left(n\right)-c \frac{n}{2}\log_{2}(2)\right)+2dn\\
&=2\left(c \frac{n}{2}\log_{2}(n)\right)-cn+2dn=cn\log_{2}(n) -cn+2dn≤cn\log_{2}n+dn\\
\end{align}$$
so, $P(n)$.
>
[[therefore]] by [[Principle of Mathematical Induction]], $P(n)$ for all $n≥2$.

Justify $O(n\log n)$:

Let $n_{0}=2,\alpha=2\cdot \frac{c}{\log2}$. Then, if $n≥n_{0}$, $$\alpha n\log n=2 \frac{c}{\log2}n\log n≥ \frac{c}{\log2} n\log n+cn≥cn\log_{2} n+dn≥T(n)$$
So, $T(n)=O(n\log n)$.
>[!note] 1
(a) 
>1. $f=O(g)$
>2. $f=\Omega(g)$
>3. $f=\Theta(g)$
>4. $f=O(g)$
>5. $f=\Theta(g)$
>6. $f=\Theta(g)$
>7. $f=\Omega(g)$
>
(b)
>1. Each of the subproblems of size $\frac{n}{b}$ requires $T(\frac{n}{d})$ [[Primitive Computational Step]]s by our definition of $T$. As there are $a$ subproblems, the number of [[Primitive Computational Step]]s from subproblems is $aT(\frac{n}{b})$. The steps for merging the solutions to the subproblems must be added to steps from subproblems. [[therefore]] the total [[Worst Case Run Time]] is given by the equation: $$T(n)=aT\left(\frac{n}{b}\right)+O(n^{d}) $$
>2. Rewrite the recurrence relation: $$T(n)≤aT\left(\frac{n}{b}\right)+cn^{d}$$with $c≥T(1)$ fixed.
>
>>[!proof]
Let $P(n)$ be that $T(n)≤cn^{d}\log_{b} n+cn^{d}$. 
>>
Induction on $n$:
>>
Base Case: $n=b$. 
$$T(b)=aT\left(\frac{b}{b}\right)+cb^{d}≤ac+cb^{d}≤cb^{d}\log_{b}b+cb^{d}$$as $a=b^{d}$. So, $P(b)$.
>>
Inductive Step: Let $n\in \mathbb{N}$ with $n>b$. Suppose that $P(k)$ holds for all $b≤k<n$.
>$$T(n)≤aT\left(\frac{n}{b}\right)+cn^{d}≤a\left(c\left(\frac{n}{b}\right)^{d}\log_{b}\left(\frac{n}{b}\right)+c \left(\frac{n}{b}\right)^{d}\right)+cn^{d}$$
By the inductive hypothesis. Note: 
>>$$\begin{align}
&T(n)≤a\left(c\left(\frac{n}{b}\right)^{d}\log_{b}n-c\left(\frac{n}{b}\right)^{d}+c \left(\frac{n}{b}\right)^{d}\right)+cn^{d} \\
&≤ \frac{ac}{b^{d}}n^{d}\log_{b}(n)+cn^{d}≤cn^{d}\log_{b}(n)+cn^{d}
\end{align}$$
as $a=b^{d}$. So, $P(n)$.
>>
[[therefore]] by [[Principle of Mathematical Induction]], $P(n)$ for all $n$.
>
If $n_{0}=b$ and $\alpha=2 \frac{c}{\log b}$ , for all $n≥n_{0}$, $$T(n)≤cn^{d}\log_{b}n+cn^{d}=cn^{d}\frac{\log n}{\log b}+cn^{d}≤2 \frac{c}{\log b}\log n=\alpha n\log n$$
[[therefore]] $T(n)=O(n\log n)$.

3. $T(n)=O(n^{n})$
The most work is done on the lowest layer, so this is the only layer that matters for the [[Asymptotic Upper Bounds]]. Formally, $$L(1)≥\alpha\sum_{i=1}^{l}L(i)$$where $l$ is the number of layers ($l\sim\log_{b}n$ CHECK) and $L(i)$ measures the [[Time Complexity]] of layer $i$. So, $T=O(\sum L(i))=O(L(1))$. 

As there are $a^{\log_{b}n}$ subproblems on the first layer. $$a^{\log_{b}n}=a^\frac{\log_{a} n}{\log_{a} b}=(a^{\log_{a}n})^\frac{1}{\log_{a}b}=n^\frac{1}{\log_{a}b}$$So, $T(n)=O(L(1))=O(O(n^\frac{1}{\log_{a}b})=O(n^\frac{1}{\log_{a}b})$.

>[!note] 2
(a)
>>[!alg]
>>$$\begin{align}
&\textbf{Algorithm } \text{3-Merge}\\
&\textbf{Input: } 3 \text{ sorted lists }A,B,C\\
&\textbf{Output: } \text{A sorted list of all the elements of }A,B,\text{ and }C\\
&\text{Let } S \text{ be a list} \\
&\textbf{While } A\cup B\cup C≠\emptyset \textbf{ do:} \\
&\quad \text{Let } D \in\{A,B,C\} \text{ such that } D[0]=\min\{A[0],B[0],C[0]\} \\
&\quad \text{Append } C[0] \text{ to } S \\
&\quad \text{Remove } C[0] \text{ from } C \\
&\textbf{end while} \\
&\textbf{return } S \\
\end{align}$$
>
(b) Like [[Merge-Sort]]'s merge, $3$-merge has runtime $O(n)$, since $3$ lists of total length $n$ are iterated through once.
>
(c) $T(n)=3T\left(\frac{n}{3}\right)+O(n)$ 
Split into three subproblems of size $\frac{n}{3}$. Merge the resulting lists with runtime $O(n)$.
>
(d) As $d=1,a=3,b=3$, $T(n)=O(n\log n)$ by (1)
>
(e)
>>[!alg]
>>$$\begin{align}
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
>
(f) $k$-merge has runtime $O(n\log k+k)$. Adding $k$ elements to the priority queue has linear run time. The while loop runs $n$ times, and priority queues take $O(\log i)$ to dequeue, where $i$ is the size. A dequeue happens each iteration of the while loop. But, since $k≤n$, $O(n\log k+ k) = O(n\log k)$. [[therefore]] $O(n\log k)$ goes into the expression for $T(n,k)$. As there are $k$ subproblems, each of size $\frac{n}{k}$, the term $kT(\frac{n}{k},k)$ must be added. The recurrence relation is given by:
$$T(n,k)=kT\left(\frac{n}{k},k\right)+O(n\log k)$$
There are $\log_{k}n$ levels to the recursion tree of $k$-mergesort. At each level, the total [[Worst Case Run Time]] of $k$-merge is $O(n\log k)$. [[therefore]] $T(n,k)=O(n\log n\log k)$.


>[!note] 3


(a) $(l_{1},h_{1}),(r_{1},0)$ There is a flat line at the bottom until the left edge of the building. There is a flat line from the left edge to the right edge at the height of the building. The rest of silhouette is flat.

(b) NOT CORRECT

Merge $(x_{1},y_{1}),(x_{2},y_{2})$ and $(u_{1},z_{1}),(u_{2},z_{2})$ into a [[Sort]]ed [[List]]: $$(a_{1},b_{1}),(a_{2},b_{2}),(a_{3},b_{3}),(a_{4},b_{4})$$Let $S$ be an empty list. Add $(a_{1},b_{1})$ to $S$. If $b_{2}>b_{1}$, append $(a_{2},b_{2})$ to $S$. If $b_{3}>$ the $b$-coord of the last element of $S$, add $(a_{3},b_{3})$ to $S$. Append $(a_{4},b_{4})$ to $S$. $S$ is the merged silhouette. 

(c)
>[!alg]
>$$\begin{align}
&\textbf{Algorithm } \text{Merge Two Silhouettes}\\
&\textbf{Input: } \text{Silhouettes } S_{1},S_{2}\\
&\textbf{Output: } \text{The merged silhouette}\\
&\text{Let } S \text{ be an empty list }\\
&\textbf{While } S_{1}≠\emptyset\lor S_{2}≠\emptyset \textbf{ do:} \\
&\quad \text{Let } i \text{ be the index of the list with the smaller first } x \text{ coord}\\
&\quad \textbf{If } S==\emptyset\lor last\_added==i \lor last(S)_{y}<S_{i}[0]_{y} \textbf{ then:}\\
&\quad \quad \text{Append } S_{i}[0] \text{ to } S\\
&\quad \quad last_{added}= i\\
&\quad \textbf{end if}\\
&\quad \text{Remove } S_{i}[0]\\
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


>[!proof] Proof of Correctness with Double Induction

Let $P(n)$ be the statement that $skyline$ [[Algorithm]] works for inputs of size $n$.

Base Case: $n=1$.
Converting one building to a silhouette does not change the picture. ...


Inductive Step: let $n>1$ be given. Assume that $P(k)$ holds for all $1≤k<n$.
By the inductive hypothesis, $S_{1}$ and $S_{2}$ are two skylines that must be merged. I shall prove that $merge$ correctly merges them. 

>[!proof] Second Induction: 
Let $l$ be the sum of the lengths of $S_{1}$ and $S_{2}$.
>
Let $Q(i)$ be the statement that the merged silhouette $S$ is correct after the $i$th iteration of the loop.
>
Induction on $i$:
>
Base Case: $i=1$.
After the first iteration of the loop, we have added one point to the skyline $S$. If the first element of $S_{1}$ had a smaller $x$-value than the first element of $S_{2}$, then that point would be the first point in the skyline regardless of their $y$-values. The reverse is also true. [[therefore]] $Q(1)$.

Inductive Step: Let $i$ be given with $1≤i<l$. Assume that $Q(i)$ is true.
We are interested in the state of $S$ after the $i+1$ loop. A few cases must be considered. Case 1: $S'[0]_{y}$

[[therefore]] by [[Principle of Mathematical Induction]], $Q(i)$ for all $i≤l$.

In particular, the silhouette is correct after the $l$th (last) iteration of the while loop. So, $P(n)$.

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
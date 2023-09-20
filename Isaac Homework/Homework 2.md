<p align=center>
Homework 2 <br>
Isaac Viviano
</p>

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
>
>3. 
>The most work is done on the lowest layer, so this is the only layer that matters for the [[Asymptotic Upper Bounds]]. Formally, $$L(1)≥\alpha\sum_{i=1}^{l}L(i)$$where $l$ is the number of layers ($l\sim\log_{b}n$ CHECK) and $L(i)$ measures the [[Time Complexity]] of layer $i$. So, $T=O(\sum L(i))=O(L(1))$. 
>
As there are $a^{\log_{b}n}$ subproblems on the first layer. $$a^{\log_{b}n}=n^{\log_{b}a}$$This rule is given in the textbook. So, $T(n)=O(L(1))=O(O(n^{\log_{b}a}))=O(n^{\log_{b}a})$.

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
$$T(n,k)=kT\left(\frac{n}{k},\min\left\{k,\frac{n}{k}\right\}\right)+O(n\log k)$$
There are $\log_{k}n$ levels to the recursion tree of $k$-mergesort. At each level, the total [[Worst Case Run Time]] of $k$-merge is $O(n\log k)$. [[therefore]] $T(n,k)=O(n\log n\log k)$.


>[!note] 3


(a) $(l_{1},h_{1}),(r_{1},0)$ There is a flat line at the bottom until the left edge of the building. There is a flat line from the left edge to the right edge at the height of the building. The rest of silhouette is flat.

(b) $S$ will be the merged silhouette. Let $i$ be $1$ if $S_{1}[0]_{x}<S_{2}[0]_{x}$ and $2$ otherwise. Add $S_{i}[0]$ to $S$. Now let $j$ be $1$ if $S_{1}[1]_{x}<S_{2}[0]_{x}$ and $2$ otherwise. 

Suppose $j==i$, append $S_{i}[1]$ to $S$. If $S$






(c)
>[!alg]
>$$\begin{align}
&\textbf{Algorithm } \text{Merge} \\
&\textbf{Input: } \text{Two silhouettes }S_{0},S_{1}\\
&\textbf{Output: } \text{The merged silhouette}\\
&\text{Let }S \text{ be an empty list}\\
&indices=(0,0) \\
&\textbf{While } S_{0}[indices_{0}:]≠\emptyset\lor S_{1}[indices_{1}:]≠\emptyset \textbf{ do:} \\
&\quad \text{Pick }cur \text{ such that } S_{cur}[indices_{cur}]_{x}=\min\{S_{0}[indices_{0}]_{x},S_{1}[indices_{1}]_{x} \}  \\
&\quad oth = !cur\\
&\quad \textbf{If } indices_{oth}>0 \textbf{ then:}\\
&\quad \quad y=\max\{S_{cur}[indices_{cur}]_{y},S_{oth}[indices_{oth}-1]_{y}\} \\
&\quad \textbf{Else:} \\
&\quad \quad y = S_{cur}[indices_{cur}]_y\\
&\quad \textbf{end if} \\
&\quad x=S_{cur}[indices_{cur}]_{x} \\
&\quad \textbf{If } S==\emptyset\lor y≠last(S)_{y} \textbf{ then:} \\
&\quad \quad \text{Append } (x,y) \text{ to } S \\
&\quad \textbf{end if}\\
&\quad \text{Increment }indices_{cur}\text{ by }1\\
&\textbf{end while} \\
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
Let $Q(j)$ be the statement that the merged silhouette $S$ is correct after the $j$th iteration of the loop.
>
Induction on $j$:
>
Base Case: $j=1$.
After the first iteration of the loop, we have added one point to the skyline $S$. If the first element of $S_{1}$ had a smaller $x$-value than the first element of $S_{2}$, then that point would be the first point in the skyline regardless of their $y$-values. The reverse is also true. [[therefore]] $Q(1)$.

Inductive Step: Let $j$ with $1≤j<l$ be given. Assume that $Q(i)$ is true.
We are interested in the state of $S$ after the $j+1$ loop. A few cases must be considered. 
Case 1: we have only added points from one of the silhouettes. If the next point is from that same silhouette, clearly we can just add it (which is what happens as two consecutive points in the same silhouette cannot have the same height). Otherwise the point must be in the new silhouette. If the $y$-coord of the first point of the new silhouette is less than or equal to the $y$-value of the last point added to the merged silhouette, then the first point of the new silhouette should not be added to the skyline. Since in this case, $indices_{oth}>0,y=S_{oth}[indices_{oth}]_{y}=last(S)_{y}$, the point will not be added. If the $y$-coord of the first point of the new silhouette is greater than the $y$-coord of the last point added to the merged silhouette, then we need to add the first point of the new silhouette to the skyline. This will happen as $indices_{oth}>0,y=S_{cur}[indices_{cur}]_{y}≠last(S)_{y}$. 

Case 2: we have already added points from both silhouettes. By the inductive hypothesis, $S$ is the correct silhouette so far. To add the next point to $S$, we choose the larger $y$ value of $S_{1}$ and $S_{2}$ at the $x$. The $y$-value of $S_{cur}$ at $x$ is given by $S_{cur}[indices_{cur}]_{y}$. The $y$ value of $S_{oth}$ at $x$ is given by $S_{oth}[indices_{oth}-1]_{y}$, since this is the $y$-coord of the previous point in $S_{oth}$.

>>
[[therefore]] by [[Principle of Mathematical Induction]], $Q(j)$ for all iterations of the while loop.
>
In particular, the silhouette is correct after the last iteration of the while loop. Since we have reached the end of the area where $S_{1}$ and $S_{2}$ overlap, we may simply append the remaining points in the input silhouettes to complete the merge. [[therefore]] $P(n)$.

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
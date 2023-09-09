>[!note] 1
First, I want to explain some terminology I will use. I will divide the the wall of size $2^{n}$ into $4$ quadrants of with side lengths $2^{n-1}$.
![[FCC0C5D0-8366-4762-9622-2E0CBA2F2312_1_105_c.jpeg | 200]]
I will define an size $n$-tile [[Recursive]]ly. A $1$-tile is simply one of the given L-shaped bricks. For $n≥2$, an $n$-tile is constructed from $4$ $(n-1)$-tiles as shown:
![[81C7E693-4E99-41EA-8D75-472288FDC15E_1_105_c.jpeg | 300]]
Now for the inductive proof.
>
>>[!proof]
Let $P(n)$ be the [[Proposition]]: the $2^{n}$ wall can be tiled with the drain-pipe anywhere.
>>
Base Case: n=1
For this case, the quadrants each correspond to one of the squares. So, whichever square the pipe occupies, the pipe takes up the whole quadrant containing it. Fill three remaining squares with a $1$-tile. As this works no matter which tile the pipe is in, $P(1)$ is true.
>>
Inductive Step: Let $n≥1$ be given, assume $P(n)$ is true.
Then, a $2^{n}\times 2^{n}$ wall may be filled with L-blocks no matter where the drain pipe goes. Consider a $2^{n+1}\times2^{n+1}$ wall. Then, each quadrant is a $2^{n}\times2^{n}$ wall. Let the pipe go in any square. Whichever quadrant the pipe is in, tile with L-blocks. Note: this is possible by the inductive hypothesis. The remainder of the wall may be tiled by one $(n+1)$-tile. This fills the $2^{n+1}\times2^{n+1}$ with L-tiles no matter where the pipe is. So, $P(n)\implies P(n+1)$.
>>
[[therefore]] by the [[Principle of Mathematical Induction]], $P(n)$ for all $n\in \mathbb{N}$.

>[!note] 2
(a) Let $\text{BFS}$ take a [[node]] $v$ and [[Graph]] $G$ containing $v$. Let the [[Function]] perform a [[Breadth-First Search]] on $G$ from $v$. Let $\text{BFS}$ return the maximum [[Distance]] of any [[node]] from $v$. Here is an [[Algorithm]] to determine if a [[Graph]] has [[Diameter]] of 3.
>>[!alg]
>>$$\begin{align}
&\textbf{Algorithm } \text{Diameter of 3?} \\
&\textbf{Input: } \text{Graph } G \text{ with vertex set } V \\
&\textbf{Output: } \text{Boolean Value inducating whether } G \text{ has diameter 3} \\
&\text{Let } lst \text{ be a list with length equal to the number of vertices in } V  \\
&\text{Let } i=0\\
&\textbf{For } \text{Vertex } v\in V\textbf{ do:} \\
&\quad lst[i]=\text{BFS}(v,G)\\
&\quad i=i+1\\
&\textbf{return } \max(lst)==3
\end{align}$$
>
(b) Let $\text{BFS}$ take a [[Graph]] $G$. Let the [[Function]] pick a random [[node]] of $G$ and perform a [[Breadth-First Search]] on $G$ starting at the chosen node. Let it return the [[Breadth-First Search Tree]].
>>[!alg]
>>$$\begin{align}
&\textbf{Algorithm } \text{Tree?} \\
&\textbf{Input: } \text{Graph } G \text{ with vertex set }V \text{ edge set }E\\
&\textbf{Output: } \text{Boolean Value indicating whether } G \text{ is a Tree} \\
&\text{Let } tree = \text{BFS}(G) \\
&\text{Let } stck \text{ be a stack} \\
&\text{Let } E' \text{ and } V' \text{ be sets} \\
&\text{Push root of } tree \text{ onto } stck \\ 
&\textbf{While } stck \text{ is not empty} \textbf{ do:} \\
&\quad node = Pop(stck) \\
&\quad \textbf{For } child \text{ of } node \textbf{ do:} \\
&\quad \quad \text{Add } \{node, child\} \text{ to } E'\\
&\quad \quad \text{Push } child \text{ onto } stck\\
&\quad \textbf{end for} \\
&\quad \text{Add } node \text{ to } V' \\
&\textbf{end while} \\
&\textbf{return } V==V'\land E==E'
\end{align}$$
>
(c) Similar DFS to B
>>[!alg]
>>$$\begin{align}
&\textbf{Algorithm } \text{Cycle Contaning } v\\
&\textbf{Input: } \text{Graph }G \text{ with vertex }v\\
&\textbf{Output: } \text{Boolean indicating whether }v \text{ is contained in a cycle}\\
&\text{Let } lst=\text{DFS}(G)\\
&\textbf{For } i\text{ in } 1 \text{ to length(}lst)-1\textbf{ do:}\\
&\quad \textbf{If } v==lst[i] \textbf{ then:}\\
&\quad \quad \textbf{return } \text{true}\\
&\textbf{return } \text{false}\\
\end{align}$$

>[!note] 3
(a) Consider the [[Worst Case Run Time]] that occurs when both numbers are [[String]]s of $n$ $1$s. Then, $k-1$ bitwise additions are required for the $2^{k}$-th place. So, to add the two [[Binary]] numbers, $$\sum_{k=1}^{n}k-1≤\sum_{k=1}^{n}k=\frac{n(n+1)}{2}$$This is $O(n^2)$ by the [[Asymptotic Tight Bound for Polynomials Proposition]].
>
(b) Let P(n) be the [[Proposition]] $n!≤n^{n}$. I will prove that $P(n)$ is true for $n\in \mathbb{N}$.
Base case: $n=1$
As $1!=1$ and $1^{1}=1$, $P(1)$ is true.
Inductive Step: Let $n\in \mathbb{N}, n≥1$ be given, and assume $P(n)$ is true.
Then, $$(n+1)!=(n+1)\cdot n!≤(n+1)\cdot n^{n}≤(n+1)\cdot(n+1)^{n}=(n+1)^{n+1}$$so, $P(n+1)$.
[[therefore]] by [[Principle of Mathematical Induction]], for all $n\in \mathbb{N}$, $n!≤n^{n}$. This implies that $n!=O(n^n)$ By the [[Asymptotic Bound of Compositions of Functions Proposition]], $$\log(n!)=\log(n^n)=n\log(n)$$
>
(c) If $n_{0}=1$ and $c=100$, for all $n≥n_{0}$, $c\cdot (2n+3)≥5n$
>
(d) If $n_{0}=1$ and $c=1$, for all $n≥n_{0}$, $c\cdot(5n)≥2n+3$

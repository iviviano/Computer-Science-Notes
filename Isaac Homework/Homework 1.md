<p align=center>
Isaac Viviano <br>
Homework 1
</p>

>[!note] 1
First, I want to explain some terminology I will use. I will divide the the wall of size $2^{n}$ into $4$ quadrants of with side lengths $2^{n-1}$.
![[FCC0C5D0-8366-4762-9622-2E0CBA2F2312_1_105_c.jpeg | 200]]
I will define a size $n$-tile [[Recursive]]ly. A $1$-tile is simply one of the given L-shaped bricks. For $n≥2$, an $n$-tile is constructed from $4$ $(n-1)$-tiles as shown:
![[81C7E693-4E99-41EA-8D75-472288FDC15E_1_105_c.jpeg | 300]]
Now for the inductive proof.
>
>>[!proof]
Let $P(n)$ be the [[Proposition]]: the $2^{n}$ wall can be tiled with the drain-pipe anywhere.
>>Induction on $n$:
Base Case: $n=1$
For this case, the quadrants each correspond to one of the squares. So, whichever square the pipe occupies, the pipe takes up the whole quadrant containing it. Fill three remaining squares with a $1$-tile. As this works no matter which tile the pipe is in, $P(1)$ is true.
>>
Inductive Step: Let $n≥1$ be given, assume $P(n)$ is true.
Then, a $2^{n}\times 2^{n}$ wall may be filled with L-blocks no matter where the drain pipe goes. Consider a $2^{n+1}\times2^{n+1}$ wall. Then, each quadrant is a $2^{n}\times2^{n}$ wall. Let the pipe go in any square. Whichever quadrant the pipe is in, tile with L-blocks. Note: this is possible by the inductive hypothesis. The remainder of the wall may be tiled by one $(n+1)$-tile. This fills the $2^{n+1}\times2^{n+1}$ with L-tiles no matter where the pipe is. So, $P(n)\implies P(n+1)$.
>>
[[therefore]] by the [[Principle of Mathematical Induction]], $P(n)$ for all $n\in \mathbb{N}$.

>[!note] 2
(a) Let $\text{BFS}$ take a [[node]] $v$ and [[Graph]] $G$ containing $v$. Let the [[Function]] perform a [[Breadth-First Search]] on $G$ from $v$. Let $\text{BFS}$ return the maximum [[Distance]] of any [[node]] from $v$ (height of [[Breadth-First Search Tree]]. Here is an [[Algorithm]] to determine if a [[Graph]] has [[Diameter]] of 3.
>>[!alg]
>>$$\begin{align}
&\textbf{Algorithm } \text{Diameter of 3?} \\
&\textbf{Input: } \text{Graph } G \text{ with vertex set } V \\
&\textbf{Output: } \text{Boolean Value inducating whether } G \text{ has diameter 3} \\
&\text{Let } set \text{ be a Set of integers}  \\
&\textbf{For } \text{Vertex } v\in V\textbf{ do:} \\
&\quad \text{Add BFS}(v,G)\text{ to } set\\
&\textbf{return } \max(set)==3
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
(c) Use the same $\text{BFS}$ function from (b), except $\text{BFS}$ accepts the starting vertex as an argument.
>>[!alg]
>>$$\begin{align}
&\textbf{Algorithm } \text{Cycle Containing } v \text{?}\\
&\textbf{Input: } \text{Graph }G \text{ with vertex }v\\
&\textbf{Output: } \text{Boolean indicating whether }v \text{ is contained in a cycle}\\
&\text{Let } tree = \text{BFS}(G,v)\\
&\text{Let } stck \text{ be a stack}\\
&\textbf{For } grandchild \text{ of root of } tree \textbf{ do:} \\
&\quad \text{Add } grandchild \text{ to } stck \\
&\textbf{end for} \\
&\textbf{While } stck \text{ is not empty} \textbf{ do:} \\
&\quad node = Pop(stck) \\
&\quad \textbf{For } \text{Edge } e\in E \textbf{ do:} \\
&\quad \quad \textbf{If } (node, v) == e \textbf{ then:} \\
&\quad \quad \quad \textbf{return } \text{true}\\
&\quad \quad \textbf{end if} \\
&\quad \textbf{end for} \\
&\quad \textbf{For } child \text{ of } node \textbf{ do:} \\
&\quad \quad \text{Push } child \text{ onto } stck \\
&\quad \textbf{end for} \\
&\textbf{end while} \\
&\textbf{return } \text{false} \\
\end{align}$$

>[!note] 3
(a) Consider the [[Worst Case Run Time]] that occurs when both numbers are [[String]]s of $n$ $1$s. Then, $2$ bitwise additions are required for each bit after the first and excluding the $n-th$ carry. So, to add the two [[Binary]] numbers, at most $2n$ bitwise additions are required. By the [[Asymptotic Tight Bound for Polynomials Proposition]], this process is $O(n)$.
>
(b) Let $P(n)$ be the [[Proposition]] $\log(n!)≤\log(n^{n})$. I will prove that $P(n)$ is true for $n\in \mathbb{N}$.
Induction on $n$:
Base case: $n=1$
As $1!=1$ and $1^{1}=1$, $P(1)$ is true.
>
Inductive Step: Let $n\in \mathbb{N}, n≥1$ be given, and assume $P(n)$ is true.
Then, $$\log[(n+1)!]=\log(n+1)+ \log(n!)≤\log(n+1)+ \log(n^{n})$$by the inductive hypothesis. As $\log$ is monotonic, $n\log(n)\le n\log(n+1)$. So,  $$\log(n+1)\log(n^{n})≤\log(n+1)+\log(n+1)^{n}=\log(n+1)^{n+1}$$so, $P(n+1)$.
[[therefore]] by [[Principle of Mathematical Induction]], for all $n\in \mathbb{N}$, $\log(n!)≤\log(n^{n})$.
>
(c) If $n_{0}=1$ and $c=100$, for all $n≥n_{0}$, $c\cdot (2n+3)≥5n$
>
(d) If $n_{0}=1$ and $c=1$, for all $n≥n_{0}$, $c\cdot(5n)≥2n+3$


Idea: 
1. Sort by $x$-value
2. Divide 
3. For merge, closest pair is either closest pair in either half, or closest from crossing halves

>[!alg]
>$$\begin{align}
&\textbf{Algorithm } \text{Closest Pairs}\\
&\textbf{Input: } \text{Set of points } S\subseteq \mathbb{R}^{2}\\
&\textbf{Output: } \text{Closest pair of points in }S\\
&\textbf{If } |S|==2 \textbf{ then:} \\
&\quad \textbf{return } S\\
&\textbf{end if} \\
&\textbf{If } |S|==3 \textbf{ then:} \\
&\quad \textbf{return } \text{brute force solution} \\
&\textbf{end if} \\
&S_{x}= \text{Sort } S \text{ by } x \text{-coordinate } (O(n\log n)\text{, but only happens at top level})\\
&S_{y}=\text{Sort }S \text{ by } y \text{-coordinate } \\
&\text{Let } Q = S\left[0:\frac{len(S)}{2}\right],R=S\left[\frac{len(S)}{2}:len(S)\right]\\
&\text{Let }(q_{0}^{*},q_{1}^{*})=closest\_pairs(Q_{x},Q_{y})\\
&\text{Let }(r_{0}^{*},r_{1}^{*})=closest\_pairs(R_{x},R_{y})\\
&merge()\\
&\textbf{return } \text{closest out of }(q_{0}^{*},q_{1}^{*}), (r_{0}^{*},r_{1}^{*}), (s_{0}^{*},s_{1}^{*})\\
&\text{}\\
&merge: \\
&\quad \text{Let } \delta=\min\{d(q_{0}^{*},q_{1}^{*}),d(r_{0}^{*},r_{1}^{*})\}\\
&\quad \text{Let } X \text{ be points within } \delta \text{ of } S\left[\frac{len(S)}{2}\right]_{x} \text{ } (O(n)) \\
&\quad \text{Sort } X \text{ by } y \text{-coordinate } (O(n\log n))\\
&\quad \text{Look over all pairs of points within }15\text{ positions of each other in }X \text{ }(O(n))\\
&\quad (s_{0}^{*},s_{1}^{*}) = \text{ closest pair in } S_{y} \text{ within } 15 \text{ spots of each other }\\
\end{align}$$

Note: can find $X$ in $merge$ in $O(n)$.

>[!proof] Proof: Any closest pair is at most 15 positions from each other in $X$.
Let $L$ be the dividing line in terms of $x$-coords. $S$ is the [[Set]] of points within $\delta$ of $L$. $S_{y}$ is set of points sorted on $y$-coordinate. If $(s,s')\in S$ and $d(s,s')<\delta$, then $s,s'$ are at most $15$ positions apart in $S_{y}$. Divide the space into boxes of size $\frac{\delta}{2}$ as shown:
![[Screenshot 2023-09-18 at 10.40.06 AM.png]]
No two points can share a box, as they would both be in $Q$ or both be in $R$ with distance less than $\delta$. If $s,s'$ are more than $16$ positions apart in $S$, then they are at least $3$ rows apart. [[therefore]] the distance between them is more than $\delta$, so there is a pair in $Q$ or $R$ that is closer than $s,s'$.



>[!note]
>Runtime is $O(n\log n)$.


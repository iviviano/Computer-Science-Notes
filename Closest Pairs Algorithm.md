
Idea: 
1. Sort by $x$-value
2. Divide 
3. For merge, closest pair is either closest pair in either half, or closest from crossing halves

>[!alg]

$$\begin{align}
&\textbf{Algorithm } \text{Closest Pairs}\\
&\textbf{Input: } \text{Set of points } S\subseteq \mathbb{R}^{2}\\
&\textbf{Output: } \text{Closest pair of points in }S\\
&\textbf{If } |S|==2 \textbf{ then:} \\
&\quad \textbf{return } S\\
&\textbf{end if} \\
&\textbf{If } |S|==3 \textbf{ then:} \\
&\quad \textbf{return } \text{brute force solution} \\
&\textbf{end if} \\
&\text{Sort } S \text{ by } x \text{-coordinate } (O(n\log n))\\
&\text{Let } Q = S\left[0:\frac{len(S)}{2}\right],R=S\left[\frac{len(S)}{2}:len(S)\right]\\
&\text{Let }(q_{0}^{*},q_{1}^{*})=closest\_pairs(Q)\\
&\text{Let }(r_{0}^{*},r_{1}^{*})=closest\_pairs(R)\\
&\text{}\\
&merge: \\
&\quad \text{Let } \delta=\min\{d(q_{0}^{*},q_{1}^{*}),d(r_{0}^{*},r_{1}^{*})\}\\
&\quad \text{Let } X \text{ be points within } \delta \text{ of } S\left[\frac{len(S)}{2}\right]_{x} \text{ } (O(n)) \\
&\quad \text{Sort } X \text{ by } y \text{-coordinate } (O(n\log n))\\
&\quad \text{Look over all pairs of points within }15\text{ positions of each other in }X \text{ }(O(n))\\

\end{align}$$

Note: can find $X$ in $merge$ in $O(n)$.

>[!proof] Proof: Any closest pair is at most 15 positions from each other in $X$.

Divide $X$ into boxes of length $\frac{\delta}{2}$. Note: no two points of $X$ can share a box, as they would be in the same set $Q$ or $R$ with a distance less that $\delta$. If $x,y\in X$, they are $≥16$ positions apart in $X$. 


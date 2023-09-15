
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
&\text{Sort } S \text{ by } x \text{-coordinate}\\
&\text{Let } Q = S[0:\frac{len(S)}{2}],R=S[\frac{len(S)}{2}:len(S)]\\
&\text{Let }(q_{0}^{*},q_{1}^{*})=closest\_pairs(Q)\\
&\text{Let }(r_{0}^{*},r_{1}^{*})=closest\_pairs(R)\\
&\
&merge: \\
&\quad \text{Let } \delta=\min\{d(q_{0}^{*},q_{1}^{*}),d(r_{0}^{*},r_{1}^{*})\}\\

\end{align}$$
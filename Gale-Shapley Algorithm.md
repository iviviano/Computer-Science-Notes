---
mathLink: G-S Algorithm
---
>[!def]
> An [[Algorithm]] that returns a [[Perfect Matching]] when applied with two [[set]]s $M = \{m_1,..., m_n\}$ and $W=\{w_1,...,w_n\}$ by taking into account preferences. 

>[!alg] 
>$$\begin{align}
&\textbf{Algorithm } \text{Gale-Shapley}\\
&\textbf{Input: } \text{Sets } M \text{ and } W \\
&\textbf{Output: } \text{A set } S \text{ of engaged pairs} \\
&\textbf{While } \text{there is a man } m \text{ who is free and hasn't proposed to every woman}\textbf{ do:} \\
&\quad \text{Choose such a man } m \\
&\quad \text{Let } w \text{ be the highest-ranked woman in } m \text{'s preference list to whom m has not yet proposed} \\
&\quad \quad \textbf{If } w\text{ is free} \textbf{ then:}\\
&\quad \quad \quad (m,w) \text{become engaged} \\
&\quad \quad \textbf{Else: } w \text{ is currently engaged to }m' \\
&\quad \quad \quad \textbf{If } w\text{ prefers }m' \text{to } m \textbf{ then:} \\
&\quad \quad \quad \quad m \text{ remains free} \\
&\quad \quad \quad \textbf{Else: } w \text{ prefers }m \text{ to } m'\\
&\quad \quad \quad \quad (m, w) \text{ become engaged}\\
&\quad \quad \quad \quad m' \text{ becomes free} \\
&\quad \quad \quad \text{Endif}\\
&\quad \quad \text{Endif}\\
&\quad \text{Endwhile}\\
& \text{Return } S\\
\end{align}$$

>[!note]
> The G-S algorithm terminates after at most $n^2$ iterations of a $while$ loop. 





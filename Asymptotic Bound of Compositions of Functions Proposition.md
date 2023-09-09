---
mathLink: asymptotic bound of compositions of functions proposition
---
>[!prop]
Let $f,g$ be [[Function]]s from $\mathbb{N}\rightarrow \mathbb{R}^{+}$ and assume $g=O(h(n))$. Then, $f\circ g=O((f\circ h)(n))$.

>[!proof]

Pick $N_{1}\in \mathbb{N},c_{1}>0\in \mathbb{R}$ such that if $n≥N_{1}$, $g(n)≤c_{1}\cdot h(n)$. 

I want this to be true but I'm not sure it is (maybe if f is continuous or monotonic?)
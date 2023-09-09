---
mathLink: an asymptotic bound applies to a sum of functions
---
>[!prop]
>If $f$ and $g$ are two [[Function]]s that share an [[Asymptotic Upper Bounds]], [[Asymptotic Lower Bound]], or [[Asymptotically Tight Bound]] $h$, then $h$ is also an [[Asymptotic Upper Bounds]], [[Asymptotic Lower Bound]], or [[Asymptotically Tight Bound]] for $f+g$.
>$$f=O(h)\land g=O(h)\implies f+g=O(h)$$
$$f=\Omega(h)\land g=\Omega(h)\implies f+g=\Omega(h)$$
$$f=\Theta(h)\land g=\Theta(h)\implies f+g=\Theta(h)$$

>[!prop] Corollary
>Let $k\in \mathbb{N}$, and let $f_{1},\ldots,f_{k}$ and $h$ be [[Function]]s such that $f_{i}=O(h)$ for all $1≤i≤k$. Then 
>$$\sum_{i=1}^{k}f_{i}=O(h)$$

>[!proof]
>Pick $c_{1}\in \mathbb{R},N_{1}\in \mathbb{R}$ such that if $n≥N_1$, $f(n)≤c_{1}h(n)$. Pick $c_{2}\in \mathbb{R},N_{2}\in \mathbb{R}$ such that if $n≥N_2$, $g(n)≤c_{2}h(n)$. Let $N=\max\{N_{1},N_{2}\}$. Then, if $n≥N$,
>$$f(n)+g(n)≤c_{1}\cdot h(n)+c_{2}\cdot h(n)=(c_{1}+c_{2})\cdot h(n)$$
>As $c_{1}+c_{2}\in \mathbb{R}$, $h$ is an [[Asymptotic Upper Bounds]] for $f+g$.

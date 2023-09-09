---
mathLink: transitivity of asymptotic growth rates
---
>[!prop]
>1. If $f$ is an [[Asymptotic Upper Bounds]] for $g$ and $g$ is an [[Asymptotic Upper Bounds]] for $h$, then $f$ is an [[Asymptotic Upper Bounds]] for $h$.
>2. If $f$ is an [[Asymptotic Lower Bound]] for $g$ and $g$ is an [[Asymptotic Lower Bound]] for $h$, then $f$ is an [[Asymptotic Lower Bound]] for $h$.
>More precisely:
>$$g=O(f)\land h=O(g)\implies h=O(f)$$
$$g=\Omega(f)\land h=\Omega(g)\implies h=\Omega(f)$$
>

>[!prop] Corollary
>If $f$ is an [[Asymptotically Tight Bound]] for $g$ and $g$ is an [[Asymptotically Tight Bound]] for $h$, then $f$ is an [[Asymptotically Tight Bound]] for $h$.

>[!proof] 
>1. Pick $c_{1}\in \mathbb{R},N_{1}\in \mathbb{N}$ such that if $n≥N_{1}$, $g(n)≤c_1\cdot f(n)$. Pick $c_{2}\in \mathbb{R},N_{2}\in \mathbb{N}$ such that if $n≥N_{2}$, $h(n)≤c_2\cdot g(n)$. Let $\mathbb{N}=\max\{N_{1},N_{2}\}$. Then, if $n≥N$,$$h(n)≤c_{2}\cdot g(n)≤c_{2}\cdot(c_{1}\cdot f(n))$$As $c_{1}\cdot c_{2}\in\mathbb{R}$, $f$ is an [[Asymptotic Upper Bounds]] for $h$.

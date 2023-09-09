---
mathLink: asymptotically tight bound
---
>[!def]
>Let $T(n)$ be a function that is the [[Worst Case Run Time]] of a certain [[Algorithm]] for input size $n$. If a function $f(n)$ is both an [[Asymptotic Lower Bound]] and an [[Asymptotic Upper Bounds]] for $T$, then we write:
>$$T(n)=\Theta(f(n))$$
>and we say that $f$ is an *asymptotically tight bound* for $T$.

From an asymptotically tight bound, we conclude that $T$ grows like $f$ up to a constant factor

>[!note] Another way to compute a asymptotically tight bound:
>Let $f$ and $g$ be two functions such that 
>$$\lim_{n \rightarrow \infty}\frac{f(n)}{g(n)}=c>0$$
>Then, $f(n)=\Theta(g(n))$.

>[!proof]
>Pick $\epsilon>0$ with $\epsilon<c$, pick $N\in \mathbb{N}$ such that $n>N$ [[implies]] $|\frac{f(n)}{g(n)}-c|<\epsilon$. Then, for $n>N$, 
>$$\frac{f(n)}{g(n)}-c<\epsilon$$
>$$f(n)<(\epsilon+c)g(n)$$
>As $\epsilon+c$ is a positive constant, $f(n)=O(g(n))$. 
>$$c-\frac{f(n)}{g(n)}<\epsilon$$
>$$f(n)>(c-\epsilon)g(n)$$
>As $c-\epsilon$ is a positive constant, $f(n)=\Omega(g(n))$
>[[therefore]] $f(n)=\Theta(g(n))$

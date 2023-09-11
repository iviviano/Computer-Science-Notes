---
mathLink: asymptotic lower bound
---
>[!def]
>Let $T(n)$ be a function that is the [[Worst Case Run Time]] of a certain [[Algorithm]] for input size $n$. Given another function $f(n)$, we define an *asymptotic lower bound* on the [[Worst Case Run Time]] of the [[Algorithm]]:
>$$T(n)=\Omega(f(n))$$
>if there exists constants $\epsilon>0$ and $n_{0}\ge0$ so that for all $n\ge n_{0}$,
>$$T(n)\le \epsilon\cdot f(n)$$
>We then say that $T$ is *asymptotically lower bounded* by $f$.

Note: $\epsilon$ must be independent of $n$.

>[!def] Alternative Definition
>$T(n)$ is $\Omega(f(n))$ if $f(n)$ is $O(T(n))$ ($T$ is an [[Asymptotic Upper Bounds]] for $f$).




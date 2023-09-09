---
mathLink: asymptotic upper bound
---
>[!def]
>Let $T(n)$ be a function that is the [[Worst Case Run Time]] of a certain [[Algorithm]] for input size $n$. Given another function $f(n)$, we define an *asymptotic upper bound* on the [[Worst Case Run Time]] of the [[Algorithm]]:
>$$T(n)=O(f(n))$$
>if there exists constants $c>0$ and $n_{0}\ge0$ so that for all $n\ge n_{0}$,
>$$T(n)\le c\cdot f(n)$$
>We then say that $T$ is *asymptotically upper bounded* by $f$.

Note: $c$ must be independent of $n$ (similar to uniform convergence)

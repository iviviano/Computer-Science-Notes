---
mathLink: Fibonacci sequence
---
>[!def]
>A sequence defined [[Recursive]]ly:
>$$a_{n+1}=a_{n}+a_{n-1}\text{ for }n>1$$
>$$a_{0}=0$$
>$$a_{1}=1$$

>[!alg]
>fib$(n)$:
>	if $n<=1$, return $n$
>	else, return fib$(n-1)+$ fib$(n-2)$
>

This is a bad [[Algorithm]]. It has poor [[Time Complexity]], since many fibonacci numbers are computed multiple times.

Let $T(n)$ be the number of calls to fib. Then,
$$T(0)=T(1)=\text{ fib}(1)$$
$$T(n)\ge T(n-1)+T(n-2)\ge2T(n-2)$$
so,
$$T(n)\ge 2^{\frac{n}{2}}$$
when $n$ is even.
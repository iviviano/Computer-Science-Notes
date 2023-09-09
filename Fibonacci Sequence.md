---
mathLink: Fibonacci sequence
---
>[!def]
>A sequence defined [[Recursive]]ly:
>$$a_{n+1}=a_{n}+a_{n-1}\text{ for }n>1$$
>$$a_{0}=0$$
>$$a_{1}=1$$

>[!alg]
>$$\begin{align}
&\textbf{Algorithm } \text{Bad Fibonacci} \\
&\textbf{Input: } \text{n} \\
&\textbf{Output: } \text{The nth Fibonacci number} \\
&\textbf{If } \text{}n≥1 \textbf{ then:}\\
&\quad \textbf{return } \text{}n \\
&\textbf{Else:} \\
&\quad \textbf{return } \text{} F_{n-1}+F_{n-2}
\end{align}$$

This is a bad [[Algorithm]]. It has poor [[Time Complexity]], since many fibonacci numbers are computed multiple times.

Let's find an [[Asymptotic Lower Bound]] for the [[Worst Case Run Time]] of our naive [[Algorithm]]: Let $T(n)$ be the number of calls to fib. Then,
$$T(0)=T(1)=\text{ fib}(1)$$
$$T(n)\ge T(n-1)+T(n-2)\ge2T(n-2)$$
so,
$$T(n)\ge 2^{\frac{n}{2}}$$
when $n$ is even. Similarly, 
$$T(n)≥2^{\frac{n}{2}-1}$$
when $n$ is odd. This may be verified with [[Principle of Mathematical Induction]].

>[!alg]
>$$\begin{align}
&\textbf{Algorithm } \text{Better Fibonacci}\\
&\textbf{Input: } \text{} n \\
&\textbf{Output: } \text{} F_{n}\\
&\text{Let lst be a list with length } n+1 \\
&\text{lst}[0]=0
&\text{lst}[1]=1\\
&\textbf{For } i\text{ in }2\text{ to } n \textbf{ do:}\\
&\quad \text{lst}[i]=\text{lst}[i-1]+\text{lst}[i-2]\\
&\textbf{return } \text{lst}[n]
\end{align}$$

Analyze the better [[Algorithm]]. 
1. Cost to fill one entry is 1 addition
2. Number of entries filled is $n+1$
Total cost: $T(n)=n+1$

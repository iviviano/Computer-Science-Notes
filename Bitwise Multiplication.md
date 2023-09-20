---
mathLink: bitwise multiplication
---

Problem: multiply two numbers $x,y$ from their bitwise representation (each $n$ bits).

>[!question]
>Is there a [[Divide and Conquer Paradigm]] [[Algorithm]] that beats the naive $O(n^{2})$?

>[!note]
>Shifting is much faster than addition or multiplication

>[!alg]
Idea: divide $x,y$ into higher and lower order bits.
>- Let $x,y$ be $n$-bit numbers
>	- Let $k=\frac{n}{2}$
>- $x_{H}$ is first $k$ bits of $x$
>- $x_{L}$ is last $k$ bits of $x$
>- Note: $x=x_{H}\cdot2^{k}+x_{L}$ so,
$$x\cdot y=(x_{H}2^{k}+x_{L})(y_{H}2^{k}+y_{L})=x_{H}y_{H}2^{n}+2^{k}(x_{L}y_{L}+x_{L}y_{H})+x_{L}y_{L}$$
[[Worst Case Run Time]] recurrence relation: $$T(n)=4T\left(\frac{n}{2}\right)+O(n)$$
From [[Homework 2]], $T(n)=O(n^{\log_{2}4})=O(n^{2})$

>[!alg]
Idea: fewer subproblems.
>- $H=x_{H}y_{H},L=X_{L}y_{L},Z=x_{H}y_{H}+x_{L}y_{L}$
>- $(x_{H}+x_{L})(y_{H}+y_{L})=H+Z+L$
>- $xy=H2^{n}+Z2^{k}+L$
>- Compute $H$
>- Compute $L$
>- $Z=(x_{H}+x_{L})(y_{H}+y_{L})-H-L$
[[Worst Case Run Time]] recurrence relation: $$T(n)=3T\left(\frac{n}{2}\right)+O(n)$$
So, $T(n)=O(n^{\log_{2}3})$.

Proof Idea: 
Base Case: $n=1$ 
Hardcode this: $O(1)$

Inductive Step: Let $n>1$ be given. Assume that it works on inputs with length $n>k≥1$.
Let $x,y$ be $n$ bits long. By inductive hypothesis, $H,L,P$ are correct. By algebra, merge step is correct.
---
mathLink: bitwise multiplication
---

Problem: multiply two numbers $x,y$ from their bitwise representation (each $n$ bits).

>[!question]
>Is there a [[Divide and Conquer Paradigm]] [[Algorithm]] that beats the naive $O(n^{2})$?

>[!note]
>Shifting is much faster than addition or multiplication

Idea: divide $x,y$ into higher and lower order bits.
- Let $x,y$ be $n$-bit numbers
	- Let $k=\frac{n}{2}$
- $x_{H}$ is first $k$ bits of $x$
- $x_{L}$ is last $k$ bits of $x$
- Note: $x=x_{H}\cdot2^{k}+x_{L}$ so,
$$x\cdot y=(x_{H}2^{k}+x_{L})(y_{H}2^{k}+y_{L})=x_{H}y_{H}2^{n}+2^{k}(x_{L}y_{L}+x_{L}y_{H})+x_{L}y_{L}$$

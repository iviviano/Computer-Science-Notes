>[!note] 1

(a) 
>[!alg]  Algorithm
>$$\begin{align}
&\textbf{Algorithm } \text{Exponentiation} \\
&\textbf{Input: } \text{Integers: }n,k\\
&\textbf{Output: } n^{k}\\
&\textbf{If } k==1 \textbf{ then:}\\
&\quad \textbf{return } n \\
&\textbf{end if} \\
&x= exp\left(n,\left\lfloor\frac{k}{2}\right\rfloor\right) \\
&\textbf{If } k \text{ is odd} \textbf{ then:} \\
&\quad \textbf{return } k\cdot x\cdot x \\
&\textbf{return } x\cdot x \\
\end{align}$$

Let $T(k)$ count the number of multiplications required to compute $n^{k}$. $T(k)$ satisfies the recurrence relation: $$T(k)≤T\left(\left\lfloor \frac{k}{2}\right\rfloor\right)+3$$as at most $3$ multiplications 

(b) 
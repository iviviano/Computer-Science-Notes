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

Let $T(k)$ count the number of multiplications required to compute $n^{k}$. $T(k)$ satisfies the recurrence relation: $$T(k)≤T\left(\left\lfloor \frac{k}{2}\right\rfloor\right)+3≤T\left(\frac{k}{2}\right)+2$$as at most $2$ multiplications occur at any particular level. So, 
...

$T(k)=O(\log k)$

(b) 

>[!alg] Algorithm 1

$$\begin{align}
&\textbf{Algorithm } \text{Tutor Hogging} \\
&\textbf{Input: } \text{Array} A \text{ of length }n\\
&\textbf{Output: } \text{} \\
&\text{Let } map \text{ be a hashmap from names to number of slots signed up for} \\
&\textbf{For } student\in A \textbf{ do:} \\
&\quad \textbf{If } student\in A \textbf{ then:} \\
&\quad \quad x = \text{ value associated with } student \\
&\quad \quad \textbf{If } x> \frac{n}{2} \textbf{ then:} \\
&\quad \quad \quad \textbf{return } student \\
&\quad \quad \textbf{end if}\\
&\quad \textbf{Else:} \\
&\quad \quad \text{Put }(student,1) \text{ in } map \\
&\quad \textbf{end if} \\
&\textbf{end for} \\
&\textbf{return } \text{false} \\
\end{align}$$

Need $n=1$ case
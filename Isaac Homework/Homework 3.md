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
>[!alg]

$$\begin{align}
&\textbf{Algorithm } \text{Exponentiation with Alien Chip} \\
&\textbf{Input: } \text{Integers }n,k \\
&\textbf{Output: } n^{k} \\
&\text{Let } A \text{ be an array of length }n+1 \text{ of }0\text{'s}\\
&A[0]=1;A[1]=k;A[2]=\text{alien\_prod}(k, k, 1) \\
&total\_remainder =0 \\
&partial = fun(k) \\
&\textbf{return } total\\
&fun(k): \\
&\quad \textbf{If } k<3 \textbf{ then:} \\
&\quad \quad \textbf{return } A[k]\\
&\quad total\_remainder =total\_remainder +k\%3\\
&\quad prev=fun\left(\left\lfloor \frac{k}{3}\right\rfloor\right) \\
&\quad A\left[\left\lfloor \frac{k}{3}\right\rfloor \right] =prev\\
&\quad \textbf{return } \text{alien\_prod}(prev,prev,prev)\\
\end{align}$$


(a) 
>[!alg] Algorithm 1
>$$\begin{align}
&\textbf{Algorithm } \text{Tutor Hogging} \\
&\textbf{Input: } \text{Array} A \text{ of length }n\\
&\textbf{Output: } \text{} \\
&\textbf{If } n==1 \textbf{ then:} \\
&\quad \textbf{return } \text{false} \\
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

Unfortunately, while this algorithm has expected runtime $O(n)$, [[Hashmap]] operations have [[Worst Case Run Time]] $O(n)$. [[therefore]] its actual [[Worst Case Run Time]] is $O(n^{2})$.

Here is an algorithm that has guaranteed runtime $O(n\log n)$, since [[AVL tree]] operations are $O(\log n)$.

>[!alg] Algorithm 2
>$$\begin{align}
&\textbf{Algorithm } \text{Tutor Hogging} \\
&\textbf{Input: } \text{Array} A \text{ of length }n\\
&\textbf{Output: } \text{} \\
&\textbf{If } n==1 \textbf{ then:} \\
&\quad \textbf{return } \text{false} \\
&\text{Let } map \text{ be an AVL treemap from names to number of slots signed up for} \\
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

(b) This [[Algorithm]] is easily generalizable to the $\frac{n}{3}$ or $\frac{n}{k}$ case. Simply replace the $$\textbf{If } x>\frac{n}{2}$$ with $$\textbf{If }x>\frac{n}{3}\text{ or }\textbf{If }x>\frac{n}{k}$$
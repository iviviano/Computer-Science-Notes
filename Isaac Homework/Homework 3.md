>[!note] 1
(a) 
>>[!alg]  Algorithm
>>$$\begin{align}
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
>
Let $T(k)$ count the number of multiplications required to compute $n^{k}$. $T(k)$ satisfies the recurrence relation: $$T(k)≤T\left(\left\lfloor \frac{k}{2}\right\rfloor\right)+3≤T\left(\frac{k}{2}\right)+2$$as at most $2$ multiplications occur at any particular level. So, 
...
>
$T(k)=O(\log k)$
>
>(b) 
>>[!alg]
>>$$\begin{align}
&\textbf{Algorithm } \text{Exponentiation with Alien Chip} \\
&\textbf{Input: } \text{Integers } n,k\\
&\textbf{Output: } n^{k}\\
&cur\_{remainder}=0\\
&\text{Let }A \text{ be an array of length }3\\
&A[0]=1;A[1]=n;A[2]=\text{alien\_prod}(n,n,1)\\
&partial=fun(k)\\
&\textbf{Switch } cur\_remainder \textbf{ do:} \\
&\quad \textbf{Case }0 \textbf{:} \\
&\quad \quad \textbf{return } partial \\
&\quad \textbf{Case } 1 \textbf{:}\\
&\quad \quad \textbf{return } \text{alien\_prod}(partial,n, 1) \\
&\quad \textbf{Case } 2 \textbf{:}\\
&\quad \quad \textbf{return } \text{alien\_prod}(partial, n, n) \\
&\text{} \\
&fun(k):\\
&\quad \textbf{If } k<3 \textbf{ then:} \\
&\quad \quad \textbf{return } A[k]\\
&\quad cur\_remainder=cur\_remainder+k\%3\\
&\quad \textbf{If } cur\_remainder≥3 \textbf{ then:} \\
&\quad \quad res = fun\left(\left\lceil \frac{k}{3}\right\rceil\right)\\
&\quad \quad cur\_remainder=cur\_remainder-3\\
&\quad \textbf{Else:} \\
&\quad \quad res=fun\left(\left\lfloor \frac{k}{3}\right\rfloor\right)\\
&\quad \textbf{end if} \\
&\quad \textbf{return } \text{alien\_prod}(res,res,res)
\end{align}$$
>
Here's the idea of the inductive proof:
The base case of $fun$ ensures that powers of $n$ less than $3$ are correct. 
>
$cur\_remainder$ remains correct at all times: If it is currently greater than or equal to $3$, then the current $k$ is not divisible by $3$. So, $$\left\lfloor \frac{k}{3}\right\rfloor < \frac{k}{3} < \left\lceil \frac{k}{3}\right\rceil\implies\left\lfloor \frac{k}{3}\right\rfloor +1=\left\lceil \frac{k}{3}\right\rceil$$so, $$fun\left(\left\lceil \frac{k}{3}\right\rceil\right)=kfun\left(\left\lfloor \frac{k}{3}\right\rfloor\right)$$so taking the product at the end does indeed reduce the current remainder by $3$.
>
Cleanup after $fun$: If after the calls to $fun$, $partial$ is the correct result, so it is returned. If there is a remainder, then we must use the alien chip to multiply in the missing terms, which is done.
>
Note: there are at most $\left\lceil\log_{3}k\right\rceil$ calls to $fun$.
>
One of the calls to $fun$ does not require a multiplication, so I will add $\log_{3}k$ multiplications from $fun$. Clearly, there are $2$ multiplications outside of $fun$. Therefore, at most $$\log_{3}k+2$$multiplications happen.

(2)
>[!note] 2
>(a) 
>>[!alg] Algorithm 1
>>$$\begin{align}
&\textbf{Algorithm } \text{Tutor Hogging} \\
&\textbf{Input: } \text{Array } A \text{ of length }n\\
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
>
Unfortunately, while this algorithm has expected runtime $O(n)$, [[Hashmap]] operations have [[Worst Case Run Time]] $O(n)$. [[therefore]] its actual [[Worst Case Run Time]] is $O(n^{2})$.
>
Here is an algorithm that has guaranteed runtime $O(n\log n)$, since [[AVL tree]] operations are $O(\log n)$.
>
>>[!alg] Algorithm 2
>>$$\begin{align}
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
>
(b) This [[Algorithm]] is easily generalizable to the $\frac{n}{3}$ or $\frac{n}{k}$ case. Simply replace the $$\textbf{If } x>\frac{n}{2}$$ with $$\textbf{If }x>\frac{n}{3}\text{ or }\textbf{If }x>\frac{n}{k}$$
and add the appropriate base cases.

>[!note] 1

(PICTURES)
(a) Here is a counterexample for $n=3$. Let $w=(3,2,1),h=(1,2,1)$. The given [[Greedy Paradigm]] [[Algorithm]] will pick rectangle $1$, the widest, and then finish as neither of the others nests inside. The correct solution is to pick rectangle $2$ first as this allows $3$ to nest inside.

(b) Here is a counterexample for $n=3$. Let $w=(10,2,1),h=(1,2,1)$, so $p=(22,8,4)$. The given [[Greedy Paradigm]] [[Algorithm]] will pick rectangle $1$, the largest perimeter, and then finish as neither of the others nests inside. The correct solution is to pick rectangle $2$ first as this allows $3$ to rest inside. 

(c) Here is a counterexample for $n=3$. Let $w=(10,2,1),h=(1,2,1)$, so $a=(10,4,1)$. The given [[Greedy Paradigm]] [[Algorithm]] will pick rectangle $1$, the largest area, and then finish as neither of the others nests inside. The correct solution is to pick rectangle $2$ first as this allows $3$ to nest inside.

(d) Here is a counterexample for $n=3$. Let $w=(10,9,1),h=(2,1,2)$, so $a=(20,9,2)$. The given [[Greedy Paradigm]] [[Algorithm]] will pick rectangle $3$, the smallest area, and then finish as it cannot nest in either of the others. The correct solution is to pick rectangle $1$ first as this allows $2$ to nest inside.

>[!note] 2

Note: this problem uses $1$-indexing.

(a) $g[1]=2,g[2]=7,g[3]=9,g[3]=10$

(b)
>[!proof]

Suppose that the algorithm returns true. I will show that $g$ gives an increasing function from $[n]$ to $[m]$.

Claim 1: $g$ is an increasing array. 

Base case: 


>[!note] 3



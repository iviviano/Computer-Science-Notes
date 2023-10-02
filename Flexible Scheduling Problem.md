---
mathLink: flexible scheduling problem
---
Time constraints:
- tasks have length $t_{i}$
- and deadlines $d_{i}$
A solution is a choice of start times $s_{i}$ for each task such that no tasks overlap

Finish times are given by $f_{i}=s_{i}+t_{i}$

Lateness penalty: $l_{i}=\max\{0,f_{i}-d_{i}\}$

Goal: minimize largest late penalty: $L=\max\{l_{i}\}$
- Note: there are other possible cost functions that might lead to different algorithms

[[Greedy Paradigm]] [[Algorithm]] ideas:
1. Longest job first
2. Shortest job first, counterexample: $t=(1,2),d=(3,2)$
3. Smallest slack time first (slack time = $d_{i}-t_{i}$), counterexample: $t=(1,3),d=(3,4)$
4. Earliest deadline 

>[!proof] Proof via [[Exchange Argument]]
Simple Case: $2$ jobs:
Assume $d_{1}≤d_{2}$. Claim: Solution $A$ (ours) has lower cost than solution $B$
Let $l_{i}^{A},l_{i}^{B}$ be the lateness in $A,B$ respectively. 
Fact $1$: $l_{1}^{A}≤l_{1}^{B}$. Job $1$ runs first in solution $A$, so the lateness of solutions $B$ cannot be less than that of solution $B$.
Fact 2: $l_{2}^{A}≤l_{1}^{B}$. Note: if $l_{2}^{A}=0$, then obviously holds. Otherwise $l_{2}^{A}=f_{2}-d_{2}=t_{1}+t_{2}-d_{2}$. 
$l_{1}^{B}=f_{1}-d_{1}=t_{2}+t_{1}-d_{1}$. (If $l_{1}^{B}$ were $0$, then $l_{2}^{A}$ would also be $0$)
As $d_{1}≤d_{2},l_{2}^{A}≤l_{1}^{B}$.
$$\therefore\max\{l_{1}^{A},l_{2}^{A}\}≤l_{1}^{B}≤\max\{l_{1}^{B},l_{2}^{B}\}$$



>[!note]
>This works for the swap of any two adjacent jobs.

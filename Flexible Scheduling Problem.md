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
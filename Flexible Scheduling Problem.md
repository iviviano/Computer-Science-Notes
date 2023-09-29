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
3. Smallest slack time first (slack time = $d_{i}-t_{i}$), counterexample: $t=(1,4),d=(4,5)$
4. Earliest deadline
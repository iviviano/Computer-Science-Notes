---
mathLink: flexible scheduling problem
---

Time constraints:
- tasks have length $t_{i}$
- and deadlines $d_{i}$
A solution is a choice of start times $s_{i}$ for each task such that no tasks overlap

Finish times are given by $f_{i}=s_{i}+t_{i}$

Lateness penalty: $l_{i}=\max\{0,f_{i}-d_{i}\}$

Goal: minimize largest late penalty: $\max\{l_{i}\}$

---
mathLink: list
---
>[!ds]
>A *list* is a [[Data Structure]] where elements are kept in order and associated with an index.

[[Array]] Implementation:
- A list can be implemented with an [[Array]]. This provides indexing into the list in $O(1)$.
- To check if the list contains an element the [[Asymptotic Upper Bounds]] $O(n)$
- If the [[Array]] elements are [[Sort]]ed, checking for an element takes $O(\log n)$ with [[Binary Sort]]

[[Linked List]] implementation:
- Indexing into the list has [[Worst Case Run Time]] $O(n)$
- To check if the list contains an element: [[Worst Case Run Time]] $O(n)$
- Much faster for frequent insertions and removals

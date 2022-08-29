# Breadth-first search
#### Algorithm for searching the nodes of a graph in order by their hop count from a starting node

Breadth-first search (BFS) is an algorithm for searching a tree data structure for a node that satisfies a given property. It starts at the tree root and explores all nodes at the present depth prior to moving on to the nodes at the next depth level. Extra memory, usually a queue, is needed to keep track of the child nodes that were encountered but not yet explored.
For example, in a chess endgame a chess engine may build the game tree from the current position by applying all possible moves, and use breadth-first search to find a win position for white. Implicit trees (such as game trees or other problem-solving trees) may be of infinite size; breadth-first search is guaranteed to find a solution node if one exists.
In contrast, (plain) depth-first search, which explores the node branch as far as possible before backtracking and expanding other nodes, may get lost in an infinite branch and never make it to the solution node. Iterative deepening depth-first search avoids the latter drawback at the price of exploring the tree's top parts over and over again. On the other hand, both depth-first algorithms get along without extra memory.

[[Depth-first search]]
[[Algorithm]]
[[Tree (data structure)]]
[[Queue (abstract data type)]]
[[Stack (abstract data type)]]
[[Artificial intelligence]]
[[Data structure]]
[[Array data structure]]
[[Hash table]]
[[Heap (data structure)]]
[[Linked list]]
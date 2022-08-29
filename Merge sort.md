# Merge sort
#### Divide and conquer-based sorting algorithm

In computer science, merge sort (also commonly spelled as mergesort) is an efficient, general-purpose, and comparison-based sorting algorithm. Most implementations produce a stable sort, which means that the order of equal elements is the same in the input and output. Merge sort is a divide-and-conquer algorithm that was invented by John von Neumann in 1945. A detailed description and analysis of bottom-up merge sort appeared in a report by Goldstine and von Neumann as early as 1948.
Conceptually, a merge sort works as follows:
Example C-like code using indices for top-down merge sort algorithm that recursively splits the list (called runs in this example) into sublists until sublist size is 1, then merges those sublists to produce a sorted list. The copy back step is avoided with alternating the direction of the merge with each level of recursion (except for an initial one-time copy, that can be avoided too). To help understand this, consider an array with two elements. The elements are copied to B, then merged back to A. If there are four elements, when the bottom of the recursion level is reached, single element runs from A are merged to B, and then at the next higher level of recursion, those two-element runs are merged to A. This pattern continues with each level of recursion.

[[Array data structure]]
[[Computer science]]
[[Queue (abstract data type)]]
[[Stack (abstract data type)]]
[[Quicksort]]
[[Insertion sort]]
[[Processor (computing)]]
[[Binary search algorithm]]
[[Heapsort]]
[[Linked list]]
[[Linux]]
[[Python (programming language)]]
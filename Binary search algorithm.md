# Binary search algorithm
#### Search algorithm finding the position of a target value within a sorted array

In computer science, binary search, also known as half-interval search, logarithmic search, or binary chop, is a search algorithm that finds the position of a target value within a sorted array. Binary search compares the target value to the middle element of the array. If they are not equal, the half in which the target cannot lie is eliminated and the search continues on the remaining half, again taking the middle element to compare to the target value, and repeating this until the target value is found. If the search ends with the remaining half being empty, the target is not in the array.
There are numerous variations of binary search. In particular, fractional cascading speeds up binary searches for the same value in multiple arrays. Fractional cascading efficiently solves a number of search problems in computational geometry and in numerous other fields. Exponential search extends binary search to unbounded lists. The binary search tree and B-tree data structures are based on binary search.
Binary search works on sorted arrays. Binary search begins by comparing an element in the middle of the array with the target value. If the target value matches the element, its position in the array is returned. If the target value is less than the element, the search continues in the lower half of the array. If the target value is greater than the element, the search continues in the upper half of the array. By doing this, the algorithm eliminates the half in which the target value cannot lie in each iteration.

[[Array data structure]]
[[Computer science]]
[[Tree (data structure)]]
[[Central processing unit]]
[[Quicksort]]
[[Merge sort]]
[[Binary tree]]
[[Database]]
[[Hash table]]
[[Java (programming language)]]
[[C (programming language)]]
[[Python (programming language)]]
[[Data structure]]
[[Algorithm]]
[[Heap (data structure)]]
[[Linked list]]
[[Queue (abstract data type)]]
[[Stack (abstract data type)]]
[[Breadth-first search]]
[[Depth-first search]]
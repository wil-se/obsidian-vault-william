# Hash table
#### Associative array for storing key–value pairs

In computing, a hash table, also known as hash map, is a data structure that implements an associative array or dictionary. It is an abstract data type that maps keys to values. A hash table uses a hash function to compute an index, also called a hash code, into an array of buckets or slots, from which the desired value can be found. During lookup, the key is hashed and the resulting hash indicates where the corresponding value is stored.
Ideally, the hash function will assign each key to a unique bucket, but most hash table designs employ an imperfect hash function, which might cause hash collisions where the hash function generates the same index for more than one key. Such collisions are typically accommodated in some way.
In a well-dimensioned hash table, the average time complexity for each lookup is independent of the number of elements stored in the table. Many hash table designs also allow arbitrary insertions and deletions of key–value pairs, at amortized constant average cost per operation.

[[Data structure]]
[[Computer memory]]
[[Software]]
[[Computer architecture]]
[[Linked list]]
[[JavaScript]]
[[Java (programming language)]]
[[Python (programming language)]]
[[Stack (abstract data type)]]
[[Queue (abstract data type)]]
[[Array data structure]]
[[Tree (data structure)]]
[[Heap (data structure)]]
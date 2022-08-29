# CPU time
#### Time used by a computer

CPU time (or process time) is the amount of time for which a central processing unit (CPU) was used for processing instructions of a computer program or operating system, as opposed to elapsed time, which includes for example, waiting for input/output (I/O) operations or entering low-power (idle) mode. The CPU time is measured in clock ticks or seconds. Often, it is useful to measure CPU time as a percentage of the CPU's capacity, which is called the CPU usage. CPU time and CPU usage have two main uses.
The CPU time is used to quantify the overall empirical efficiency of two functionally identical algorithms. For example any sorting algorithm takes an unsorted list and returns a sorted list, and will do so in a deterministic number of steps based for a given input list. However a bubble sort and a merge sort have different running time complexity such that merge sort tends to complete in fewer steps. Without any knowledge of the workings of either algorithm a greater CPU time of bubble sort shows it is less efficient for particular input data than merge sort.
This type of measurement is especially useful when comparing like algorithms that are not trivial in complexity. In this case the wall time (actual duration elapsed) is irrelevant, the computer may execute the program slower or faster depending on real world variables such as the CPU's temperature, as well as other operating system variables, such as the process's priority.

[[Central processing unit]]
[[Computer program]]
[[Operating system]]
[[Merge sort]]
[[System call]]
[[Linux]]
[[Parallel computing]]
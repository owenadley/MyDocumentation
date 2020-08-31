********************************
Algorithms
********************************

Dynamic Programming
^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^
Dynamic programming problems are problems that have optimal sub-structure or overlapping subproblems.
If some problem instances can be seen as pieces of other problem instances, we can store our work along the way to avoid doing the same work twice.
Dynamic programming is caching the results of the subproblems of a problem, so that every subproblem is solved only once.

1. Optimal sub-structure: You can break a problem down into smaller and smaller chunks and then combine them to get the optimal solution 
(If you can solve a problem recursively, then it have optimal sub-structure).

2. Overlapping subproblems: Re-computing the same thing more than once. DP works by caching those values so that we dont need to recompute.

* You can use DP in problems that contain minimization (shortest maze path, smallest coins), maximization (longest maze path), optimization or counting.
* If you can solve a problem by enumeration all possible options and then taking the best one its probably DP.

Examples:
https://leetcode.com/problems/unique-paths/
https://leetcode.com/problems/maximal-square/

Depth First Search
^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^
* Uses a stack. Either your own or the call stack via recursion
* LIFO
* Uses: backtracking, complete search, exhausting possible paths


Breadth First Search
^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^
* Iterative with a queue
* FIFO
* Uses: Check if a path exists between nodes, finding "hops" or distance out or "levels" away
# Divide and Conquer Algorithm

A **divide and conquer algorithm** is a strategy of solving a large problem by

1. breaking the problem into smaller sub-problems
2. solving the sub-problems, and
3. combining them to get the desired output.

To use divide and conquer algorithms, **recursion** is used.

> **How Divide and Conquer Algorithms Work?**

This technique can be divided into the following three parts:

1. **Divide**: Divide the given problem into sub-problems using recursion.
2. **Conquer**: Sub-problem by calling recursively until sub-problem solved.
3. **Combine**: Combine the solutions of the sub-problems that we will get find problem solution.

> **Complexity**

The complexity of the divide and conquer algorithm is calculated using **the master theorem**.

```
T(n) = aT(n / b) + f(n),
where,
n = size of input
a = number of subproblems in the recursion
n / b = size of each subproblem. All subproblems are assumed to have the same size.
f(n) = cost of the work done outside the recursive call, which includes the cost of dividing the problem and cost of merging the solutions
```

Let us take an example to find the time complexity of a recursive problem.

For a merge sort, the equation can be written as:

```
T(n) = aT(n / b) + f(n)
	 = 2T(n / 2) + O(n)
Where,
a = 2 (each time, a problem is divided into 2 subproblems)
n / b = n / 2 (size of each sub-problem is half of the input)
f(n) = time taken to divide the problem and merging the subproblems
T(n / 2) = O(nlogn) 

Now, T(n) = 2T(nlogn) + O(n) = O(nlogn)
```

> **Applications**

1. Binary Search
2. Merge Sort
3. Quick Sort
4. Strassen's Matrix Multiplication
5. Closest Pair of Points
6. Karatsuba Algorithm

> **Divide and Conquer vs Dynamic Programming**

The divide and conquer approach divides a problem into smaller subproblems, these subproblems are further solved recursively. The result of each subproblem is not stored for future reference, whereas, in a dynamic programming approach, the result of each subproblems is stored for future reference.

Use the divide and conquer approach when the same subproblem is not solved multiple times. Use the dynamic programming approach when the result of a subproblem is to be used multiple times in the future.

Both paradigms divide the given problem into subproblems and solve subproblems. How to choose one of them for a given problem? Divide and conquer should be used when same subproblems are not evaluated many times. Otherwise dynamic programming or memoization should be used. For example, binary search is a divide and conquer algorithm, we never evaluate the same subproblems again. On the other hand, for calculating nth Fibonacci number, dynamic programming should be preferred.
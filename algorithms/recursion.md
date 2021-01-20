# Recursion

> **What is Recursion?**

Any function which calls itself is called *recursive*.

A recursive method solves a problem by calling a copy of itself to work on a smaller problem. This is called the recursion step. The recursion step can result in many more such recursive calls.

It is important to ensure that the recursion terminates. Each time the function calls itself with a slightly simpler version of the original problem. The sequence of smaller problems must eventually converge on the base case.

> **Why Recursion?**

Recursion is a generally shorter and easier to write than iterative code. Generally, loops are turned into recursive functions when they are are compiled or interpreted.

Recursion is most useful for tasks that can be defined in terms of similar subtasks. For example, sort, search, and traversal problems often have simple recursive solutions.

> **Format of a Recursive Function**

Base case where the function does not recur or terminate.

Recursive case where the function calls itself to perform a subtask.

```
if (test for the base case)
	return some base case value
else if (test for another base case)
	return some other base case value
else
	return (some work and then a recursive call)
```

As an example consider the factorial function: n! is the product of all integers between n and 1. In the base case, when n is 0 or 1, the function simply returns 1. In the recursive case, when n is greater than 1, the function calls itself to determine the value of (n - 1)! and multiplies that with n.

```
int fact(int n) {
	if (n <= 1)
		return 1;
	
	return n * fact(n - 1);
}
```

> **Recursion and Memory**

Each recursive call makes a new copy of that method in memory. Once a method ends (that is, returns some data), the copy of that returning method is removed from memory. The recursive solutions look simple but visualization and tracing takes time.

> **Recursion versus Iteration**

1. **Recursion**
   * Terminates when a base case is reached
   * Each recursive call requires extra space on the stack frame (memory)
   * If we get infinite recursion,  the program may run out of memory and result in stack overflow
   * Solutions to some problems are easier to formulate recursively
2. **Iteration**
   * Terminates when a condition is proven to be false
   * Each iteration does not require extra space
   * An infinite loop could loop forever since there is no extra memory being created
   * Iterative solutions to a problem may now always be as obvious as a recursive solution

> **Notes on Recursion**

* Recursive algorithms have two types of cases, recursive cases and base cases.
* Every recursive function case must terminate at a base case.
* Generally, iterative solutions are more efficient than recursive solutions due to the overhead of function calls.
* A recursive algorithm can be implemented without recursive function calls using a stack, but it's usually more trouble than its worth. That means any problem that can be solved recursively can also be solved iteratively.
* For some problems, there are no obvious iterative algorithms.
* Some problems are best suited for recursive solutions while others are not.

> **Example Algorithms of Recursion**

1. Fibonacci Series, Factorial Finding
2. Merge Sort, Quick Sort
3. Binary Search
4. Tree Traversals and many Tree Problems: Inorder, Preorder, Postorder
5. Graph Traversals: DFS and BFS
6. Dynamic Programming Examples
7. Divide and Conquer Algorithms
8. Towers of Hanoi
9. Backtracking Algorithms
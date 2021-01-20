# Greedy Algorithms

> **Introduction**

Let us start our discussion with simple theory that will give us an understanding of the Greedy technique. In the game of *Chess*, every time we make a decision about a move, we have to also think about the future consequences. Whereas, in the game of *Tennis (or Volleyball)*, our action is based on the immediate situation.

This means that in some cases making a decision that looks right at that moment gives the best solution (*Greedy*), but in other cases it doesn't. The Greedy technique is best suited for looking at the immediate situation.

> **Greedy Strategy**

Greedy algorithms work in stages. In each stage, a decision is made that is good at that point, without bothering about the future. This means that some *local best* is chosen. It assumes that a local good selection makes for a global optimal solution.

> **Elements of Greedy Algorithms**

The two basic properties of optimal Greedy algorithms are:

1. Greedy choice property
2. Optimal substructure

**Greedy choice property**

This property says that the globally optimal solution can be obtained by making a locally optimal solution (Greedy). The choice made by a Greedy algorithm may depend on earlier choices but not on the future. It iteratively makes one Greedy choice after another and reduces the given problem to a smaller one.

**Optimal substructure**

A problem exhibits optimal substructure if an optimal solution to the problem contains optimal solutions to the subproblems. That means we can solve subproblems and build up the solutions to solve larger problems.

> **Does Greedy Always Work?**

Making locally optimal choices does not always work. Hence, Greedy algorithms will not always give the best solutions.

> **Advantages and Disadvantages of Greedy Method**

The main advantage of the Greedy method is that it is straightforward, easy to understand and easy to code. In Greedy algorithms, once we make a decision, we do not have to spend time re-examining the already computed values. Its main disadvantage is that for many problems there is no greedy algorithm. That means, in many cases there is no guarantee that making locally optimal improvements in a locally optimal solution gives the optimal global solution.

> **Greedy Applications**

* Sorting: Selection sort, Topological sort
* Priority Queues: Heap sort
* Huffman coding compression algorithm
* Prim's and Kruskal's algorithms
* Shortest path in Weighted Graph [Dijikstra's]
* Coin change problem
* Fractional Knapsack problem
* Disjoint sets-Union by size and Union by height (or rank)
* Job scheduling algorithm
* Greedy techniques can be used as an approximation algorithm for complex problems
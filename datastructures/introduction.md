> What is data?

Data is a collection of raw facts and data structures provide a way of storing and organizing this data in a structured way.

There are two types of data types:

1. System-defined data types (also called primitive data types)
2. User-defined data types

> What is Data Structures?

Data structure is a particular way of storing and organizing data in a computer so that it can be used efficiently. A data structure is a special format for organizing and storing data.

Depending on the organization of elements, data structures are classified into two types:

1. Linear data structures: Elements are accessed in a sequential order but it is not compulsory to store all elements sequentially. Examples: Linked Lists, Stacks, Queues etc.
2. Non-Linear data structures: Elements of this data structures are stored/accessed in a non-linear order. Examples: Trees and graphs. 

> What is an Algorithm?

An algorithm is step-by-step unambigiuous instructions to solve a given problem.

> Why the Analysis of Algorithms?

Algorithm analysis helps us to determine which algorithm is most efficient in terms of time and space consumed. 

> What is Running Time Analysis?

It is process of determining how processing time increases as the size of the problem (input size) increases.  Input size is the number of elements in the input, and depending on the problem type, the input may be of different types. The following are the common types of inputs.

* Size of an array
* Polynomial degree
* Number of elements in a matrix
* Number of bits in the binary representation of the input
* Vertices and edges in a graph

> How to Compare Algorithms? 

* <b>Execution times?</b> Not a good measure as execution times are specific to a particular computer.
* <b>Number of statements executed?</b> Not a good measure, since the number of statements varies the programming language as well as the style of the individual programmer.
* <b>Ideal solution?</b> Let us assume that we express the running time of a given algorithm as a function of the input size n and compare these different functions corresponding to running times. This kind of comparison is independent of machine time, programming style, etc.

> What is Rate of Growth?

The rate at which the running time increases as a function of input is called rate of growth. Let us assume that you go to a shop to buy a car and a bicycle. If your friend sees you there and asks what you are buying, then in general you say buying a car. This is because the cost of the car is high compared to the cost of the bicycle.

> Time Complexity

* O(1) : Constant time
* O(logn) : Logarithmic time
* O(n) : Linear time
* O(n logn) : Linear Logarithmic time
* O(n ^ 2) : Quadratic time
* O(n ^ 3) : Cubic time
* O(2 ^ n) : Exponential time 

> Types of Analysis

To analyze the given algorithm, we need to know with which inputs the algorithm takes less time and with which inputs the algorithm takes a long time. That means we represent the algorithm with multiple expressions: 

* <b>Worst case</b>
  * Defines the input for which the algorithm takes a long time
  * Input is the one for which the algorithm runs the slowest

* <b>Best case</b>
  * Defines the input for which the algorithm takes the least time
  * Input is the one for which the algorithm runs the fastest
* <b>Average case</b>
  * Provides a prediction about the running time of the algorithm
  * Run the algorithm many times, using many different inputs 

- Big-O Notation [Upper Bounding Function]

- Omega Notation [Lower Bounding Function]

- Theta Notation [Order Function]

<b>Lower Bound <= Average Time <= Upper Bound</b>
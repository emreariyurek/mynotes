# Stack

> **What is a Stack?**

A stack is a linear data structure that follow the Last In First Out (LIFO) principle. The last item to be inserted into a stack is the first one to be deleted from it.

> **Stack Operations**

1. **push**: inserts data onto stack
2. **pop**: removes the last inserted element from the stack
3. **top**: returns the last inserted element without removing it
4. **size**: returns the number of elements stored in the stack
5. **empty**: indicates whether the stack is empty or not
6. **full**: indicates whether the stack is full or not

> **Stack Implementations**

There are many ways of implementing stack.

1. *Simple Array Implementation*

This implementation of stack uses an array. In the array, we add elements from left to right and use a variable to keep track of the index of the top element. The array storing the stack elements may become full.

Limitations: The maximum size of the stack must first be defined and it cannot be changed.

| Operations | Time Complexity |
| ---------- | --------------- |
| push       | O(1)            |
| pop        | O(1)            |
| size       | O(1)            |
| empty      | O(1)            |
| full       | O(1)            |

2. *Dynamic Array Implementation*

It improves the complexity by using the array doubling technique. If the array is full, create a new array of twice the size, and copy the items. With this approach, pushing n items takes time proportional to n (not n^2).

| Operations | Time Complexity                |
| ---------- | ------------------------------ |
| push       | O(1) (Amortized constant time) |
| pop        | O(1)                           |
| top        | O(1)                           |
| size       | O(1)                           |
| empty      | O(1)                           |
| full       | O(1)                           |

3. *Linked List Implementation*

The other way of implementing stacks is by using Linked lists. Push operation is implemented by inserting element at the beginning of the list. Pop operation is implemented by deleting the node from the beginning.

| Operations | Time Complexity           |
| ---------- | ------------------------- |
| push       | O(1) (Amortized constant) |
| pop        | O(1)                      |
| top        | O(1)                      |
| size       | O(1)                      |
| empty      | O(1)                      |

**Comparing Array Implementation and Linked List Implementation**

1. Array Implementation

* Operations take constant time
* Expensive doubling operation every once in a while
* Any sequence of n operations (starting from empty stack) - "amortized" bound takes time proportional to n

2. Linked List Implementation

* Grows and shrinks gracefully
* Every operation takes constant time 
* Every operation uses extra space and time to deal with references

> **Stack Applications**

1. Balancing of symbols
2. Infix-to-postfix conversion
3. Evaluation of postfix expression
4. Implementing function calls (including recursion)
5. Finding of spans (finding spans in stock markets)
6. Page-visited history in a web browser
7. Undo sequence in a text editor
8. Matching tags in html and xml
9. Auxiliary data structure for other algorithms (ex: tree traversal algorithms)

> **Stack Problems**
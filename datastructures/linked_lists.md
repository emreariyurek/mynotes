# Linked List

> **What is a Linked List?**

A linked list is a linear data structure, in which the elements are not stored at contiguous memory locations. The elements in a linked list are linked using pointers. In simple words, a linked list consists of nodes where each node contains a data field and a reference (link) to the next node in the list. 

> **Why Linked List instead of arrays?**

Arrays can be used to store linear data of similar types, but arrays have the following limitations.

* The size of the arrays is fixed.
* Inserting a new element in an array of elements is expensive because the room has to be created for the new elements and to create room existing elements have to be shifted.

> **Advantages**

* _Dynamic size:_ Linked list is a dynamic data structure so it can grow and shrink at runtime by allocating and deallocating memory. So there is no need to give the initial size of linked list, unlike arrays.
* _Ease of insertion / deletion:_ Insertion and deletion of nodes are really easier. Unlike array here we don't have to shift elements after insertion or deletion of an element. In a linked list we just have to update the pointer of node.
* _No Memory Wastage:_ As the size of a linked list can increase or decrease at run time so there is no memory wastage. In case of an array, there is a lot of memory wastage. For example, if we declare an array of size 10 and store only 6 elements in it then space of 4 elements are wasted. There is no such problem in linked lists as memory is allocated only when required.

> **Disadvantages**

* Random access is not allowed
* Extra memory space for a pointer is required with each element of the list
* Not cache friendly. Since array elements are contiguous locations, there is locality of reference which is not there in case of linked lists
* Reverse traversing is really difficult. In case of doubly linked list its easier but extra memory is required for back pointer hence wastage of memory 

> **Types of Linked List**

* _Singly Linked List:_ Item navigation is forward only
* _Doubly Linked List:_ Items can be navigated forward and backward
* _Circular Linked List:_ Last item contains link of the first element as next and the first element has a link to the last element as previous

> **Linked List Operations**

1. Insertion
   * Inserting a new node at the beginning
   * Inserting a new node at the end of the list
   * Inserting a new node at the random location
2. Deletion
   * Deleting the first node
   * Deleting the last node
   * Deleting an intermediate node
3. Traversing
   * Searching an element using the given key

> **Time Complexity**

| Operations                   | Time Complexity                                              |
| ---------------------------- | ------------------------------------------------------------ |
| indexing                     | O(n)                                                         |
| insert / delete at beginning | O(1)                                                         |
| insert / delete at end       | O(1) when last element is known, O(n) when last element is unknown |
| insert / delete in middle    | search time + O(1)                                           |
| wasted space                 | O(n) for pointers                                            |

> **Linked List Problems**
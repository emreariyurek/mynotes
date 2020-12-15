# Tree

A tree is an example of a non-linear data structure. A tree structure is a way of representing the hieararchial nature of a structure in a graphical form. In trees, the order of the elements is not important.

* The root of a tree is the node with no parents. There can be at most one root node in a tree.
* An edge refers to the link from parent to child.
* A node with no children is called *lead node*.
* Children of same parent are called *siblings*.
* A node p is an *ancestor* of node q if there exists a path from root to q and p appears on the path. The node q is called a *descendant* of p.
* The set of all nodes at a given depth is called the *level* of the three. The root node is at level zero.
* The *depth* of a node is the length of the path from the root to the node.
* The *height* of a node is the length of the path from that node to the deepest node. The height of a tree is the length of the path from the root to the deepest node in the tree.
* *Height of the tree* is the maximum height among all the nodes in the tree and *depth of the tree* is the maximum depth among all the nodes in the tree.
* The size of a node is the number of descendants it has including itself.

# Binary Tree

A tree is called *binary tree* if each node has two children at most. Empty tree is also a valid binary tree.

> **Basic Operations**

* Inserting an element into a tree
* Deleting an element from a tree
* Searching for an element
* Traversing the tree

> **Auxiliary Operations**

* Finding the size of the tree
* Finding the height of the tree
* Finding the level which has maximum sum
* Finding the least common ancestor (LCA) for a given pair of nodes, and many more

> **Applications of Binary Trees**

* Expression trees and used in compilers
* Huffman coding trees that are used in data compression algorithms
* Binary Search Tree which suppors search, insertion and deletion on a collection of items in logarithmic time (average)
* Priority Queue which supports search and deletion of minimum or maximum on a collection of items in logarithmic time (in worst case)

> **Binary Tree Traversals**

1. **Preorder Traversal**

* Visit the root
* Traverse the left subtree 
* Traverse the right subtree

```c++
// Root - Left - Right
void preorder(Node *root) {
	if (!root)
		return;
	
	cout << root->val << endl;
  preorder(root->left);
  preorder(root->right);
}

Time Complexity: O(n), Space Complexity: O(n)
```

*Non-Recursive Preorder Traversal*

```c++
/*
	1. Create an empty stack and push root to it
	2. Pop all items one by one. Do following for every popped
		a) Print it
		b) Push its right child
		c) Push its left child
*/
void preorder(Node *root) {
  if (!root)
    return;
  
  stack<Node *> coll;
  coll.push(root);
  while (!coll.empty()) {
    Node *node = coll.top();
    coll.pop();
    cout << node->val << endl;
    if (node->right)
      coll.push(node->right);
    if (node->left)
      coll.push(node->left);
  }
}

Time Complexity: O(n), Space Complexity: O(n)
```

2. **Inorder Traversal**

* Traverse the left subtree
* Visit the root
* Traverse the right subtree

```c++
// Left - Root - Right
void inorder(Node *root) {
  if (!root)
    return;
  
  inorder(root->left);
  cout << root->val << endl;
  inorder(root->right);
}

Time Complexity: O(n), Space Complexity: O(n)
```

*Non-Recursive Inorder Traversal*

```c++
/*
	1. Create an empty stack
	2. Initialize current node as root
	3. Push the current node to stack and set curr = curr->left 		    until curr is null
	4. If current is null and stack is not empty then
		a) Pop the top item from stack
		b) Print the popped item, set curr = popped_item->right
		c) Go to step 3
	5. If current is null and stack is empty then we are done
*/
void inorder(Node *root) {
	if (!root)
    return;
  
  stack<Node *> coll;
  Node *curr = root;
  while (curr || !coll.empty()) {
  	while (curr) {
      coll.push(curr);
      curr = curr->left;
    }
    curr = coll.top();
    coll.pop();
    std::cout << curr->val << " ";
    curr = curr->right;
  }
}

Time Complexity: O(n), Space Complexity: O(n)
```

3. **Postorder Traversal**

* Traverse the left subtree
* Traverse the right subtree
* Visit the root

```c++
// Left - Right - Root
void postorder(Node *root) {
  if (!root)
    return;
  
  postorder(root->left);
  postorder(root->right);
  cout << root->val << " ";
}

Time Complexity: O(n), Space Complexity: O(n)
```

*Non-Recursive Postorder Traversal (Using Two Stacks)* 

```c++
/*
	1. Push root to first stack
	2. Loop while first stack is not empty
		a) Pop a node from first stack and push it to second stack
		b) Push left and right children of the popped node to first stack
	3. Print contents of second stack
*/
void postorder(Node *root) {
  if (!root)
    return;
  
  stack<Node *> coll, coll2;
  coll.push(root);
  while (!coll.empty()) {
    Node *curr = coll.top();
    coll.pop();
    coll2.push(curr);
    if (curr->left)
      coll.push(curr->left);
    if (curr->right)
      coll.push(curr->right);
  }
  
  while (!coll2.empty()) {
    cout << coll2.top() << " ";
    coll2.pop();
  }
} 

Time Complexity: O(n), Space Complexity: O(n)
```

*Non-Recursive Postorder Traversal (Using One Stack)*

```c++
/*
	1. Create an empty stack
	2. Do following while root is not null
	 a) Push root's right child and then root to stack
	 b) Set root as root's left child
	3. Pop an item from stack and set it as root
	 a) If the popped item has a right child and the right child is at top of stack, then remove the right child from stack, push the root back and set root as root's right child
	 b) Else print root's data and set root as null
	4. Repeat steps 2 and 3 while stack is not empty
*/
void postorder(Node *root) {
  if (!root)
    return;
  
  stack<Node *> coll;
  do {
    while (root) {
      if (root->right)
        coll.push(root->right);
      coll.push(root);
      root = root->left;
    }
    root = coll.top();
    coll.pop();
    
    if (root->right && coll.top() == root->right) {
      coll.pop();
      coll.push(root);
      root = root->right;
    } else {
      cout << root->val << " ";
      root = nullptr;
    }
  } while (!coll.empty())
}
```

4. **Level Order Traversal**

* Visit the root
* While traversing level keep all the elements at level
* Go to the next level and visit all the nodes at that level
* Repeat this until all levels are completed

```c++
void levelorder(Node *root) {
  if (!root)
    return;
  
  queue<Node *> coll;
  coll.push(root);
  while (!coll.empty()) {
    Node *node = coll.front();
    cout << node->val << " ";
    if (node->left)
    	coll.push(node->left);
    if (node->right)
      coll.push(node->right);
    coll.pop();
  }
}

Time Complexity: O(n), Space Complexity: O(n)
```

# Binary Search Tree


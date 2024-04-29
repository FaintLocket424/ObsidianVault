---
tags:
  - degree/ads/datastructures/trees
aliases:
  - Binary Tree
---
![[Trees MOC 🌍]]

A tree whose elements have at most 2 children is called a binary tree.

The children are usually called the left and right child.

> [!warning] 
> These are two different binary trees.
> ![[IMAGE binary trees with one node.png]]
> As one has a left child and the other has a right child.

---
### Terminology

##### Rooted
One node is designated as the topmost, where all nodes are descendants of this one.

##### Size
The **size** of a binary tree is the number of nodes in it.

##### Node Depth
The **depth** of a node is its distance from the root. The root is depth 0. You can just count the number of edges between it and the 

##### Tree Depth
The **depth** of the tree is the depth of it's deepest node.

##### Sibling Nodes
Two nodes with the same parent are called **siblings**.

##### Tree Edges
An **edge** is the link between two nodes.

---
### Properties

Let $T$ be a rooted binary tree of height $h$. Then:
- $T$ has at most $2^{h+1}$ nodes.
- $T$ has at most $2^{h}$ leaves.

---
### Example: Arithmetic Expressions as a binary tree

An arithmetic expression can be represented by a binary tree whose leaves are variables or constants, and the internal nodes are binary operators.

The expression:
$$
((((3+1)\times 3)/((9-5)+2))-((3\times (7-4))+6))
$$
would be:

![[IMAGE arithmetic expression as binary tree.png]]

---
### Binary Trees in Computer Science

When representing a binary tree in a computer, it's very similar to a linked list.

Each node would have:
- A pointer to its parent
- A pointer to the left child
- A pointer to the right child
- It's data

It can then be navigated like a list.

---
### Why store data this way?

It's very fast to insert, lookup and delete data, *if done correctly*.

---
### Array representation of binary tree

![[Pasted image 20240129231014.png]]

One advantage of the array-based representation is that a position $p$ can be represented by a single integer.

However, basically everything else about it is terrible.
- Space usage depends greatly on the shape of the tree. (see the gaps in the array).
- Some update operations cannot be supported efficiently. E.g. deleting a node and promoting it's child takes $O(n)$ because all descendants of the node have to move.

---
### Searching a Rooted Binary Tree

![[Pasted image 20240129174757.png]]

To search this, you start at the root and check each node in each level until you find what you're looking for.

This is the same as searching a linked list, $O(n)$.

To get better performance, we must use a [[Binary Search Tree]]. These organise the nodes for better searching.
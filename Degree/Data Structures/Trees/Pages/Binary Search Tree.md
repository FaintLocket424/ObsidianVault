---
tags:
  - degree/ads/datastructures/trees
aliases:
  - BST
---
![[Trees MOC 🌍]]

A binary search tree is a [[Rooted Binary Tree]] with one [[#The BST Property|additional property]].

![[Pasted image 20240129175404.png]]

---
### The BST Property

> [!info] 
> For all nodes $v$ in a binary search tree:
> - All elements in the left sub-tree must be "smaller" than $v$.
> - All elements in the right sub-tree must be "larger" than $v$.

Smaller and larger are subjective, depending on the data type being stored. But as long as you're consistent, it's fine.

> [!danger] 
> **You must make sure not to violate this property when manipulating a BST**.

---
### BST Operations
#### Inserting into a BST

If there are no nodes, then the inserted node becomes the root.

If the tree has nodes, traverse the tree until you find a null pointer. Go left if the insertion is smaller and go right if the insertion is bigger than the current node.

---
#### Searching a BST

First start at the root node.

- If the node is equal to the target, you've found the node.
- If the node is smaller than the target, look at the right child.
- If the node is bigger than the target, look at the left child.

---
#### Deleting from a BST

The most difficult operation on a BST.

First we have to [[#Searching a BST|Search the BST]] to find the node to remove. If that returns nothing then we're done.

How easy the deletion will be is based on the number of children the target node has.

##### No Children
If the node is a leaf then simply remove it.

##### 1 Child
If the node has one child then remove the node and put the child in its place.

##### 2 Children
If the node has two children, find the smallest node that is bigger than the target and move that node to the target's place.

![[Pasted image 20240129230207.png]]

Finding the smallest node bigger than the target is done by moving right once, then moving left to the end.

The tree would also me maintained if the largest node smaller than the target was swapped in.

---
### Complexity

For searching, insertions and deletions it's $O(h)$ where $h$ is the [[Rooted Binary Tree#Tree Depth|height of the tree]].

In the average case $h=\log n$.

The worst case is $h=n$.

>[!tip] 
>This worst case can be avoided by using balanced trees like [[AVL Trees]].


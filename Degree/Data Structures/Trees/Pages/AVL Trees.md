---
tags:
  - degree/ads/datastructures/trees
---
![[Trees MOC 🌍]]
### AVL Trees

An AVL tree is a Self-Balancing BST that follows the [[#Height-Balance Property]].

BSTs are good if they are balanced as they can be searched, inserted and deleted at $O(\log n)$. But if they degenerate, they approach their worst-case of $O(n)$.

There are many ways to avoid degeneration and AVL is just one of them.

---
### Inventors

Named after the inventors Georgy Adelson and Evgenii Landis.

---
### Height-Balance Property

> [!tldr] Height-Balance Property
> For each node $v$, the heights of $v$'s children differ by at most 1.

---
### Node Heights
- The height of NULL is 0.
- The height of a leaf is 1.
- The height of a parent is the max height of a child plus one.

The height of an AVL tree storing $n$ keys is $O(\log n)$.
![[Pasted image 20240124122259.png]]

---
### Example:

![[IMAGE unbalanced binary tree.png]]
This [[Binary Search Tree]] would be an AVL because the [[#Height-Balance Property]] is satisfied.

---
### Operations Cause Problems

The standard [[Binary Search Tree#BST Operations|BST Operations]] in AVL trees take $O(\log n)$ time.

But insertion and deletion can potentially violate the [[#Height-Balance Property]]. So, a method is needed to restore it, preferably in $O(\log n)$ time.

[[Binary Tree Rotations#Trinode Restructuring|Trinode Restructuring]] may be useful for this.

---
### Inserting into AVL

Take this valid AVL tree.
![[Pasted image 20240130143432.png]]

There are 4 cases where a rebalancing may need to occur:

##### An insertion into the left subtree of the left child of a node

![[Pasted image 20240130143602.png]]
After inserting a node into $A$, the [[#Height-Balance Property]] is now violated at $j$. This can be remedied by doing a [[Binary Tree Rotations#Right-Rotation|Right-Rotation]] between $k$ and $j$.

![[Pasted image 20240130144115.png]]

##### An insertion into the right subtree of the right child of a node

This requires a left rotation of the root and right child.
Similar to [[#An insertion into the left subtree of the left child of a node]]

##### An insertion into the right subtree of the left child of a node

![[Pasted image 20240130144839.png]]
After an insertion into the right child of the left child, the [[#Height-Balance Property]] at $j$ is violated.

A simple right rotation will not fix this so we need to delve deeper. If we look at the subtree $B$ closer, we can solve this.

![[Pasted image 20240130145312.png]]

Splitting $B$ into two different trees means we can move those subtrees around with a [[Binary Tree Rotations#Left-Rotation|Left-Rotation]] of $k$ and $i$, then a [[Binary Tree Rotations#Right-Rotation|Right-Rotation]] of $j$ and $i$.

![[Pasted image 20240130150243.png]]

##### An insertion into the left subtree of the right child of a node

For this, split the left subtree into two trees of it's root node. Then do a [[Binary Tree Rotations#Right-Rotation|Right-Rotation]] of the subtree root and it's parent. Then a [[Binary Tree Rotations#Left-Rotation|Left-Rotation]] of the root and the right child.

Similar to [[#An insertion into the right subtree of the left child of a node]]

---
#### Post-Insertion fix-up algorithm

When we insert node $p$ into the tree, we can do a simple "search and repair" method:
- From $p$, go upwards towards the root and change the height values of the nodes.
- Look for the first node which is unbalanced.
- Do a [[Binary Tree Rotations#Trinode Restructuring|Trinode Restructuring]] on the unbalanced node and the next two children on the path to $p$.

---
#### Insertion Complexity

The standard insertion for AVL trees is $O(\log n)$.

Travelling up the tree to find the unbalanced node is $O(\log n)$, and then doing the trinode restructuring is $O(1)$.

So, the worst-case running time is $O(\log n)$.

---
### Deletion from AVL

A standard [[Binary Search Tree#Deleting from a BST|BST Deletion]] can violate the [[#Height-Balance Property]] and so it may need to be fixed after deletion.

#### Post-Deletion Fix-Up Algorithm

Let $p$ be the parent of the deleted node. There may be unbalanced nodes on the path from $p$ to the root.

Fix-Up Method:
- Let $z$ be the first unbalanced node on the path.
- Let $y$ be the taller child of $z$, which will be the one not on the path.
- Let $x$ be the taller child of $y$, or the one on the same side as $y$ if they're the same.
- Do [[Binary Tree Rotations#Trinode Restructuring|Trinode Restructuring]] on $z$ - $y$ - $x$.
- Keep going up the tree, balancing nodes.

---
#### Deletion Complexity

A standard BST deletion in AVL is $O(\log n)$.

The fix-up is $O(1)$ per level.
Done at most once per level, and the height is $O(\log n)$.

All in all, the worst-case is $O(\log n)$.

---
### Unifying the Insertion and Deletion Fix-Up Algorithms

- They both trace upwards from a node.
- They both use trinode restructuring when an unbalanced node is found.

They can stop the fixing when:
- Reach an ancestor who's height didn't change.
- Trinode restructuring of a subtree results in the same height as before the insertion/deletion.

---
### Overall Complexity

For an AVL tree storing $n$ items:
- Data structure uses $O(n)$ space.
- A single restructure takes $O(1)$
- Searching takes $O(\log n)$ time
- Insertion takes $O(\log n)$ time.
- Removal takes $O(\log n)$ time.
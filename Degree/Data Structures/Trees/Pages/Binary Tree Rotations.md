---
tags:
  - degree/ads/datastructures/trees
---
![[Trees MOC 🌍]]

### Rotations

BST Rotations are either left or right rotations.
They preserve the BST property.

>[!attention] 
>- A left rotation assumes the right child is not NULL
>- A right rotation assumes the left child is not NULL

Rotations are local operations and modify a constant number of parent child links. And as such only take $O(1)$ time.

##### Left-Rotation

![[Pasted image 20240129235203.png]]

This involves making $y$ the new root and $x$ the left child of $y$. Then, making the left child of $y$ the right child of $x$, and the right child of $y$ remains so.

##### Right-Rotation

A right rotation is the opposite of a [[#Left-Rotation]]. Taking $x$ and making it the root, and $y$ it's right child. Then moving the right child of $x$ to the left child of $y$.

![[tree rotations.gif]]

---
### Trinode Restructuring

Combining multiple rotations to rebalance a tree is called trinode restructuring.

These are local operations and as such still take $O(1)$ time.

##### Single Rotation

When the child and the grandchild are on the same side.

###### Right/Right
![[Pasted image 20240130001358.png]]

When both child and grandchild are on the right, we do a left rotation on $z$.

![[Pasted image 20240130001433.png]]

###### Left/Left
![[Pasted image 20240130001538.png]]

When both child and grandchild are on the left, we do a [[#Right-Rotation]] on $z$.

![[Pasted image 20240130001615.png]]

##### Double Rotation

When the child and grandchild are not on the same side.

###### Right/Left
![[Pasted image 20240130001809.png]]

When the child is on the right and the grandchild on the left, we do a [[#Right-Rotation]] on $y$, then a [[#Left-Rotation]] on $z$.

![[Pasted image 20240130002119.png]]

###### Left/Right
![[Pasted image 20240130002135.png]]

When the child is on the left and the grandchild is on the right, we do a [[#Left-Rotation]] on $y$ then a [[#Right-Rotation]] on $z$.

![[Pasted image 20240130002231.png]]
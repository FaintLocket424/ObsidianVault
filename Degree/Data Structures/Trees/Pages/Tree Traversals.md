---
tags:
  - degree/ads/datastructures/trees
---
![[Trees MOC 🌍]]

To traverse a tree is to visit each node in the tree exactly once.

> [!note] Note
> Tree traversals are naturally recursive.

There are 6 different ways to traverse a tree.
- root, left, right (Preorder)
- left, root, right (Inorder)
- left, right, root (Postorder)

- root, right, left
- right, root, left
- right, left, root

---
### Preorder Traversal

In preorder, the root is visited first.

Root, left, right

![[Pasted image 20240129175404.png]]

For this tree, the output would be:
8, 3, 1, 6, 4, 7, 10, 14, 13

---
### Inorder Traversal

Inorder traversals visit the root in the middle.

Left, root, right

![[Pasted image 20240129175404.png]]

An inorder traversal on this tree would be:
1, 3, 4, 6, 7, 8, 10, 13, 14

An inorder traversal sorts the elements in the BST.

---
### Postorder Traversal

In postorder traversals, the root is visited last.

left, right, root

![[Pasted image 20240129175404.png]]

A postorder traversal on this tree would be:
1, 4, 7, 6, 3, 13, 14, 10, 8

---
### "Flags"

The order nodes are visited can be determined by imagining there is a "flag" attached to each node.

![[IMAGE tree traversal flags.png]]
---
tags:
  - degree/ads/datastructures/trees
---
![[Trees MOC 🌍]]

### (Binary) Heaps

Heaps are trees, but they are typically assumed to be stored in a flat array.

Physically they are a linear array. But logically. it's a binary tree, filled on all levels except the lowest.

Each node corresponds to an element of the array.

The tree is complete except the lowest level which is filled from left to right.

![[Pasted image 20240130233416.png]]

It has to fill from left to right, hence why $b$ is not full but $c$ is.
And it can only be missing nodes on the bottom layer, hence why $e$ is not full.

>[!warning] 
>Heaps are not binary **search** trees. They are just binary trees. They do not organise the data like BSTs do.

---
### Types of Heaps

##### Max Heap
The value of a node is no greater than it's parent.
$$
\text{Node value}\le\text{Parent Value}
$$
The largest element is stored at the root
In any subtree, no values are bigger than the subtree root.

![[IMAGE max heap binary tree.png]]

##### Min Heap
The value of a node is no smaller than it's parent.
$$
\text{Node value}\ge\text{Parent Value}
$$
The smallest element is stored at the root
In any subtree, no values are smaller than the subtree root.

---
### Heap Properties

Heaps have two properties, the length and the heap size.

The length is the length of the array being used to store it.
The heap size is the number of nodes in the heap.
$$
\text{Length} \ge \text{Heap Size}
$$
The height of a heap is always $\lfloor{\log n}\rfloor$

---
### Building a Heap

![[Pasted image 20240130234823.png]]

You fill from left to right. These would be the indexes that the nodes would be stored at.

---
### Insertion into a Heap

To insert an element into a heap, you add it to the end of the array, at the bottom. Then, if it's bigger than it's parent, you swap it with its parent. Then check the parent of that and so on until you get to the root.

>[!important] 
>Swapping nodes based on their values is to [[#Heapify|Heapify]].

---
### Parent-Child Index Relationships

Let's say we store our heap in array $A$.

>[!warning] 
>We use 1-indexing here.

The root is at $A[1]$.

For a node at index $I$:
- Left child is at $2I$
- Right child is at $2I+1$
- Parent is at $\lfloor \frac{I}{2} \rfloor$

---
### Why use Heaps?

Heaps are a good data structure for priority queues and sorting.

If given a sequence of objects with different priorities, you can deal with the one with the highest priority first.

Heaps make it very fast to extract the largest element.

- Largest element will be at $A[1]$.
- Set the last element in the array to $A[1]$.
- [[#Heapify]].

![[Pasted image 20240131002554.png]]
This would be the outcome of extracting the largest item, 54 from this heap.

---
### Heapify

![[Pasted image 20240131000359.png]]
Following an extraction of the largest item, the last item is then placed at the top. We now need to heapify to turn it back into a proper heap.

The algorithm for this is to:
- Start at the root with node $v$. Find node $w$, which is the largest out of $v$ and it's children.
- If $v \ne w$, swap them then recurse again with node $w$.

![[Pasted image 20240131000805.png]]

A simple algorithm for this is:
```python
def Heapify(A, v, n)
# A is the heap array
# v is the index being analysed
# n is the heap size

largest = v
# Find the largest among v and 2v (left child)
if (2v <= n) and (A[2v] > A[largest]):
	largest = 2v

# Find the largest among the current largest and the right child
if (2v+1 <= n) and (A[2v+1] > A[largest]):
	largest = 2v+1

if largest != v:
	A[v], A[largest] = A[largest], A[v]
	Heapify(A, largest, n)
```

The runtime of this algorithm is $O(\log n)$. Swapping takes $\Theta(1)$ time and it will run at most the height of the tree which is $O(\log n)$.

---
### Heap Building

Creating a heap from an arbitrary array $A$ is quite a simple task.

Simply call the Heapify function on each index, starting at the end.

```python
for i in range(heap_size, 0, -1):
	Heapify(A, i, heap_size)
```

The time complexity of building a heap is $O(n)$.

---
### Heap Sort

To sort an array using a heap, we:
- Build a heap with the unsorted data
- Starting at the end of the heap, we:
	- move the last item to the top (moving the largest to the end)
	- Decrease the heap size by one to "forget" about that largest value
	- Heapify the value placed at the root.
	- Repeat with the next node from the end.

Here's an algorithm for it.

```python
BuildHeap(A, Length(A))

for i in range(Length(A), 1, -1):
	A[i], A[1] = A[1], A[i]
	HeapSize(A) -= 1
	Heapify(A, 1, HeapSize(A))
```

The runtime of this algorithm is $O(n \log n)$.
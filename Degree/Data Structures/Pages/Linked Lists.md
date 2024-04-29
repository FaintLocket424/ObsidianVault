---
tags:
  - degree/ads/datastructures
aliases:
  - Linked List
---
![[Data Structures MOC 🌍]]

### The Singly Linked List

Linked lists are made up of nodes where each node stores some data and a pointer to the next node in the list.

The first node in the list is the head.
The last node in the list is the tail.

Nodes are not [[Contiguity|Contiguous]] in memory, they can be scattered.
The data inside a linked list can be either [[Homogeneity|Homogeneous]] or [[Heterogeneity|Heterogeneous]], it depends on the implementation.

![[Pasted image 20231021192450.png]]

---
### The Node

A node is a small data structure that stores 2 pieces of information in a linked list.

| Node N | Pseudocode |                              |
| ------ | ---------- | ---------------------------- |
|  data  |   `N.data`   | The information being stored |
|  next  |   `N.next`   |  A pointer to the next Node  |

The next property of the final node in the list points to a NULL value by convention.

---
### Properties of the Linked List

When compared to [[Arrays]], a Linked List gives up [[Contiguity]] in memory in favour of better performance in operations like deletion but sacrifices performance in other operations like element access because of it.

A linked list is defined by 3 properties:

| List L | Pseudocode |                                        |
| ------ | ---------- | -------------------------------------- |
|  head  |   `L.head`   | A pointer to the first node in the list|
|  tail  |   `L.tail`   | A pointer to the last node in the list |
|  size  |   `L.size`   |          How long is the list          |

##### So how do we access items from the linked list?

We could create a function like `L.find(i)` which finds the ith piece of data within the list. Due to the Non-[[Contiguity|Contiguous]] nature of the linked list, this is a more complex function than [[Arrays]].

This is one implementation of the `find(i)` method.
```
N=L.head
if i > L.size then
	return out of range
end if

N=L.head

if i = 1 then
	return N.data
end if

for j=2 to i do
	N = N.next
next j

return N.data
```
Here we first check if we're looking for an element outside the bounds of the list and throw an error if so. Else, we check if we're looking for the first element in the list and return the data straight away if so. If not, we traverse down the `next` pointers the required number of times until we should be at the data index required then return it.

This code will work but it's notable for its use of the `size` parameter of the list. It may not always be preferable to use the size of the list since then you need to keep track of the size during runtime which could cause bugs or introduce overhead.

##### What about deleting an element?

Deleting elements from a linked list is easier than an [[Arrays|Array]] but comes with the cost of having to ensure all the references to that node are updated.

###### Deleting the head node:

```
if L.head == NULL then
	return no head to delete
end if

if L.head = L.tail then
	L.head = NULL
	L.tail = NULL
	L.size = L.size - 1
	return
endif

L.head = L.head.nex
L.size = L.size - 1
```
Deleting the head node is fairly straightforward. First we check if the `head` points to `NULL`. This would indicate there are no items in the list and so there is no element to delete.
After that we check if the `head` and the `tail` point to the same `Node`. This indicates there is only 1 element in the list and therefore we can set both the `head` and `tail` to `NULL` and decrease the size as we now have an empty list.
And finally, if we have a longer list, we can simply move the head pointer to the pointer of the head node, thereby pointing the head to the 2nd item in the list, and decreasing the size by 1.

###### Inserting a `Node` M with data $v$ after the `Node` N in `Linked List` L:

```
Node M
M.data = v

M.next = N.next
N.next = M

if L.tail = N then
	L.tail = M
end if
```

Inserting a new node after a given node is very easy, assuming you can keep all your references in check.
First you need to create the new node and assign it's data.
Then we set the next node after M to the the current one after N.
Then we change N's next to M.
The order here is important as if we set N.next first then we would lose where the node after N is.
Finally we check if we're adding to the tail and update it accordingly.

---
### The Doubly Linked List

A node in a doubly linked list stores two references instead of one.
A next link which points to the next node and an additional prev link that points to the previous node.

Further, we add two dummy or sentinel nodes at the ends of the doubly linked list.
- The header has a next reference and a NULL prev reference.
- The trailer has a prev reference and a NULL next reference.
These nodes do not contain any data.

A doubly linked list stores references to these two sentinel nodes and a size counter (not including sentinels).

![[Pasted image 20231021192255.png]]

###### Deleting an element from a doubly linked list:

Here we want to remove Node N from the list L
```
N_prev = N.prev
N_next = N.next

N_prev.next = N_next
N_next.prev = N_prev

L.size = L.size - 1
```
- With this algorithm, we save the previous and next pointers from the elements we're deleting.
- Then we set the previous element's next pointer to the node after N.
- And we set the next node's previous pointer to the node before N.
- And then we reduce the size variable.

---
### The Circularly Linked List

The circularly linked list has the same nodes as a singly linked list but it has no beginning or end. It's like a singly linked list but the final element points to the first element.

Instead of referencing the head or the tail, we use a cursor which points to the node we want to start traversing at.

![[Pasted image 20231021192850.png]]


---
tags:
  - degree/ads/datastructures
---
![[Data Structures MOC 🌍]]

### The Queue

A queue is a collection of objects that are inserted and removed according to the [[FIFO]] principle.

Elements can only be accessed and deleted from the **front** of the queue.

Element insertion can only be done at the **rear** of the queue.

---
#### Supported Methods
- $enqueue(e)$: Insert element $e$ at the **rear** of the queue.
- $dequeue()$: Remove and return the element at the **front** of the queue. Throws an error is the queue is empty.
- $size()$: Returns the number of elements in the queue.
- $isEmpty()$: Returns true if the queue is empty.
- $front()$: Returns the front element of the queue without removing it. Throws an error if the queue is empty.
---
#### Example Queue
For our queue $Q$:

- `Q.enqueue(5)`
	- $Q=\left\{5\right\}$
- `Q.enqueue(3)`
	- $Q=\left\{5, 3\right\}$
`- Q.dequeue()`
	- $Q=\left\{3\right\}$
- `Q.enqueue(7)`
	- $Q=\left\{3, 7\right\}$
- `Q.dequeue()`
	- $Q=\left\{7\right\}$
- `Q.front()`
	- Returns $7$
- `Q.dequeue()`
	- $Q=\left\{\right\}$
- `Q.dequeue()`
	- Throws error: trying to dequeue and empty queue.

---
#### Implementation with [[Arrays]]

If we have an array $A$ of 6 elements:

|Index|0|1|2|3|4|5|
|-|-|-|-|-|-|-|
|Value| | | | | | |
|$f$|\*| | | | | |
|$r$|\*| | | | | |

We also have two variables, $f$ and $r$.

$f$ is the index of the front of the queue.
$r$ is the index where new data is to be inserted.

To start with:
$f=0$
$r=0$

When we do `A.enqueue(5)` on the array, we input the value at index $r$.

|Index|0|1|2|3|4|5|
|-|-|-|-|-|-|-|
|Value|5| | | | | |
|$f$|\*| | | | | |
|$r$||\*| | | | |

And now:
$f=0$
$r=1$

Doing 2 more enqueues for $3$ and $6$ gets us

|Index|0|1|2|3|4|5|
|-|-|-|-|-|-|-|
|Value|5|3|6| | | |
|$f$|\*| | | | | |
|$r$||| |\*| | |

With:
$f=0$
$r=3$

Now when we dequeue an item we look at the index $f$.

|Index|0|1|2|3|4|5|
|-|-|-|-|-|-|-|
|Value||3|6| | | |
|$f$||\*| | | | |
|$r$||| |\*| | |

With:
$f=1$
$r=3$

When we dequeue two more times, $f$ will equal $r$ and that means the queue is empty.

|Index|0|1|2|3|4|5|
|-|-|-|-|-|-|-|
|Value|||| | | |
|$f$||| |\*| | |
|$r$||| |\*| | |

$f=3$
$r=3$

---
This could cause an issue when after a series of enqueues and dequeues leaves you at the end of the array with no more space.

This issue can be solved with modulo arithmetic where $f$ and $r$ wrap around back to $0$.
When we increment $f$ or $r$, we do
$$(f+1)\bmod N$$
where $N$ is the length of the array.

Therefore, to get the size of the queue, we use $(r-f)\bmod N$

---

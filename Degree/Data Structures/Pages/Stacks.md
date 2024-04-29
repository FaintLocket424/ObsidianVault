---
tags:
  - degree/ads/datastructures
---
![[Data Structures MOC 🌍]]

### The Stack

A stack is a collection of objects that are inserted and removed according to the [[LIFO]] principle.

The most recently added item will be the one that comes out first.

A stack has the methods:
- `push(e)` which inserts element `e` at the top of the stack.
- `pop` which removes and returns the top element, throwing an error if the stack is empty.
- `size` which returns the number of elements in the stack
- `isEmpty` which returns a Boolean indicating if the stack is empty
- `top` which returns the top element without moving it, throwing an error if the stack is empty.

Example of the effect of these methods on the stack $S$:
- `push(5)`: $S=\left\{5\right\}$
- `push(3)`: $S=\left\{5, 3\right\}$
- `pop`: $S=\left\{3\right\}$
	- Output: 5
- `push(7)`: $S=\left\{3, 7\right\}$
- `pop`: $S=\left\{7\right\}$
	- Output 3
- `top`: $S=\left\{7\right\}$
	- Output 7
- `pop`: $S=\left\{\right\}$
	- Output 7
- `pop`: Error since stack is empty

---
### Stack Implementation using [[Arrays]]

With an array based implementation, the stack consists of an $N$-element array $S$ with an integer $t$ that holds where the top of the stack is.

$t=-1$ initially as that indicates an empty stack.

Here we implement some methods:

```
size
	return t+1
```

```
isEmpty
	return (t < 0)
```

```
top
	if isEmpty then
		throw an empty stack exception
	end if
	
	return S[t]
```

```
push(e)
	if size = N then
		throw a full stack exception
	end if
	
	t = t + 1
	S[t] = e
```

```
pop
	if isEmpty then
		throw an empty stack exception
	end if
	
	e = S[t]
	S[t] = NULL
	t = t - 1
	return e
```

Implementing a stack with an array is time efficient. Each method is independent of the size of the array.

However, the fixed size of the array can cause issues since if it's too big, we will waste memory. But if it's too small, we can generate exceptions.

The fixed size in general can be an issue.
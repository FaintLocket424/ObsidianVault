---
tags:
  - degree/ads/algorithms
---
![[Algorithms MOC 🌍]]

### The Factorial Function

$$5!=5\times4\times3\times2\times1$$

We can break that down into $5!=5\times4!$

So $n!=n\times(n-1)!$

So we can implement factorials using recursion since the function can be solved with itself.

```
if n=1 then
	return 1
else
	return n * factorial(n-1)
end if
```

---
### Properties of Recursive Algorithms

- Must have a base case.
- Must change its state and move toward the base case.
- Must call itself recursively.

---
### Memoization

A recursive implementation of the function to compute the nth Fibonacci number will be called several times with the same argument.

Instead of recalculating the answer every time, we could store the results of those function calls.

Storing the result of a computation so it can be retrieved later is called memorization.

Hash tables are a good choice of data structure for implement this.

---
### Backtracking

A technique for problems with many candidate solutions but too many to try.

E.g. there are like 6e21 possible ways to fill in a sudoku grid.

The idea is that you build up a solution 1 step at a time and backtrack when you reach an invalid path.

```
If current solution is valid then
	if current solution is complete then
		return current solution
	else
		for each extension of the current solution do
			extend_solution(extension)
		end for
	end if
end if
```


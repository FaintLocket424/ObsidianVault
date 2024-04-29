---
tags:
  - incomplete
  - degree/ads/algorithms
---
![[Algorithms MOC 🌍]]

An insertion sort on the list $(a_{1}, \ldots, a_{n})$ would look like:
```Pseudocode
for j = 2 to n do
	x = a[j]
	i = j - 1
	while i > 0 and a[i] > x do
		a[i+1] = a[i]
		i = i - 1
	end while
	a[i+1] = x
end for
```

We know that:
- When $j$ has a certain value, it inserts the $j$-th element into already sorted sequence $(a_{1}, \ldots, a_{j-1})$ so that $(a_{1}, \ldots, a_{j})$ is sorted.
- After the $j$-th iteration, the first $j+1$ elements are sorted.
- The run time is between $n+1$ and $\frac{n(n-1)}{2}$ making this an $O(n^{2})$ algorithm.

---
### Additional Information

- [Wikipedia]
- [[ADS Part 2 Asymptotic Notation.pdf#page=41|Insertion Sort Lecture Notes]]
- [Maybe Practical Q and As]

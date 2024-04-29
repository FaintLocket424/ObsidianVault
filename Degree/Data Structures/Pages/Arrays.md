---
tags:
  - degree/ads/datastructures
aliases:
  - Array
---
![[Data Structures MOC 🌍]]

### The Array

A sequence of elements $a_1,a_2,...,a_n$ is called an array and is usually denoted by something like $A[1],A[2],...,A[n]$ or $A[1 ...n]$.

Arrays are:
- **[[Contiguity|Contiguous]]** - Elements are stored in consecutive memory cells.
- **[[Homogeneity]]** - All elements are the same type.

These properties makes it easy to do certain operations like accessing elements but difficult to do others like deleting elements.

---
### Properties of the Array

|Index|1|2|3|4|5|6|7|
|-|-|-|-|-|-|-|-|
|Value|P|a|r|t|y|NULL||
|Address|0x3412|0x3413|0x3414|0x3415|0x3416|0x3417|0x3418|


##### So how do we access items from the array?

Say we have a pointer $k$ which points to the address of the first item in the array. So here $k=\mathtt{0x3412}$.

If we want to access the third item in the array, we can do so by computing an offset memory address. Since this array begins at 1, the third item is at an offset of $3-1=2$.

So then we access the memory at $k+2=\mathtt{0x3414}$ which is "r".
This only works because all the items in the array are a fixed width $w$. The example above assumes the items are only $w=1$ wide but if each element in the array took up $w=2$ spaces, our offset for the ith item would be $k+(i-1)w$.

##### What about deleting an element?

Deleting elements is a bit more complicated and costly. If we were to remove a single element like index 2, that would present problems if we don't do some extra work. We need to shuffle all the data after the deletion down. For large arrays this can be costly.

##### What about the size of the array?

If we assume the size of the array is fixed when we declare it. We then need to decide how long we are going to make the array. If you overestimate too much, your program will take up large amounts of memory but if you underestimate you could have a misbehaving program that may access parts of memory it shouldn't.

We could also dynamically resize the array at runtime. This could involve copying data which is costly but if you do it infrequently then it could be worth it.
---
tags:
  - degree/mathsforcs/sets
---
![[Maths For CS MOC 🌍]]
### Symbols and their meaning

Let's use the example of a set of students $S$ taking practical's $P$ and the set of practical's a student $s$ can attend as $P_s$.

Sets are denoted with $\left\{\right\}$.
Sets are **unordered**, therefore $\left\{2, 3\right\}\equiv\left\{3, 2\right\}$.
Think of sets as collections of objects.

Tuples are denoted with $\left(\right)$.
Tuples are **ordered**, therefore $\left(2,3\right)\not \equiv\left(3,2\right)$.
Think of tuples like coordinates.

Capital letters are used for sets, lower case letters used for members of set.

| Symbol | Description | Example | Example Translation |
| ------ | ----------- | ------- | ------------------- |
| $\in$ | In / member of | $s\in S$ | A student $s$ in $S$ |
| $\notin$ | Not In / not a member of | $s\notin S$ | A student $s$ not in $S$ |
| $\forall$ | For all | $\forall s\in S$ | For all students $s$ in $S$ |
| $\exists$ | There exists | $\exists s\in S$ | There exists a student $s$ in $S$ |
| $\emptyset$ | Empty Set | $P_s=\emptyset$ | There are no practicals student $s$ can attend |
| $:$ or \| | "Where" or "Such That" | See set builders below |  |
| $\cap$ |vIntersection | $A\cap B$ | The elements shared in both sets. Where they *intersect* |
| $\cup$ | Union | $A\cup B$ | The elements of set $A$ and the elements of set $B$ together. The *union* of the two sets. | 
| $\textbar A \textbar$ | Cardinality | $\textbar A \textbar$ | The number of elements in the finite set $A$ |

### Set Builder Notation

If we let $G$ be the set of all gamers, then:

$$\begin{aligned}
C=\left\{g\in G:g\text{ has an RTX 4090}\right\}
\end{aligned}$$

This would be the set of gamers which have an RTX 4090.

We could take this further.
$$\begin{aligned}
L=\left\{l\in G:l\notin C\right\}
\end{aligned}$$
This would be the set of gamers who are not in $C$, aka the gamers who do not have an RTX 4090. Another way to write this would be:
$$
L=\left\{l\in G:l\text{ does not have an RTX 4090}\right\}
$$
Same thing, different way.

We can construct even more complex sets if we want:
$$\begin{aligned}
S=\left\{n\in\mathbb{Z}:0 < n < 10,n\text{ is even}\right\}
\end{aligned}$$
The translation of this would be something like *"The elements in the set of integers between 1 and 10 where $n$ is an even number."*

---
### Writing statements about sets

If we have the set:
$$S=\left\{2,4,6,8\right\}$$
We can start to draw conclusions from this.

There can be simple things like $2\in S$ *(2 is in $S$)* and $3\notin S$ *(3 is not in S)* but we can also write longer statements like:

*If $n\in S$ then $n$ is even.*

Here $n$ acts as a temporary label to reference later the item we're talking about.

---
### Set Intersection

The intersection of two sets is where they overlap in their elements. The symbol for intersection is $\cap$. You know that because intersectioN.

$$\begin{aligned}
A&=\left\{2,3,4,5,6\right\} \\
B&=\left\{5,6,7,8,9\right\}
\end{aligned}$$

So here, $A\cap B$ would be:
$$A\cap B=\left\{5,6\right\}$$
It helps visualise it if the sets are lined up:
$$\begin{aligned}
A&=\left\{2,3,4,5,6\right\} \\
&\quad\quad B=\left\{5,6,7,8,9\right\}
\end{aligned}$$

---
### Set Union

The union of two sets is the combined set of all their elements. The symbol for union is $\cup$. You know that because **U**nion.

$$\begin{aligned}
A&=\left\{2,3,4,5,6\right\} \\
B&=\left\{5,6,7,8,9\right\}
\end{aligned}$$

So here, $A\cup B$ would be:
$$A\cup B=\left\{1,2,3,4,5,6,7,8,9\right\}$$

---
### Principle of inclusion-exclusion

If you have two finite sets then you can say:
$$\begin{aligned}
|A\cup B|=|A|+|B|-|A\cap B|
\end{aligned}$$

This is just saying the number of elements in the union of $A$ and $B$ is just the number in $A$ plus the number in $B$ minus all the duplicates.

An example of a question like this would be:
*In a group of 100 persons, 72 people can speak English and 43 can speak French. How many can speak English only? How many can speak French only and how many can speak both English and French?*

From this information we can say that:
$$\begin{aligned}
E&=\left\{\text{English Speakers}\right\} \\
F&=\left\{\text{French Speakers}\right\} \\\\
|E|&=72 \\
|F|&=43 \\
|E\cup F|&=100
\end{aligned}$$

From this we can learn how many speak both French and English:
$$\begin{aligned}
|E\cup F|&=|E|+|F|-|E\cap F| \\\\
\therefore|E\cap F|&=|E|+|F|-|E\cup F| \\\\
|E\cap F|&=72+43-100 \\
&=15
\end{aligned}$$
We now know the number that speak both languages is 15.

So then the number of English only speakers is $72-15=57$ and the number of French only speakers is $43-15=28$.

---
### Subsets

Let's say we have the sets:
$$\begin{aligned}
G&=\left\{g\in\text{Gamers}:g\text{ has a graphics card}\right\} \\
E&=\left\{g\in\text{Gamers}:g\text{ has an EVGA graphics card}\right\}
\end{aligned}$$

So here we have the set $G$ of gamers with graphics cards.
And we have the set $E$ which is the set of gamers with EVGA cards specifically.

We could say that $E\subseteq G$ *($E$ is a subset of $G$)* which means every element of $E$ is also an element of $G$.
In our context this makes sense since everyone who owns an EVGA graphics card must own a graphics card.

We could take this even further and say that $E\subset G$ *($E$ is a proper subset of $G$)* which just means that $E$ is a subset of $G$ but does not equal $G$.
In our context this makes sense since not all gamers who own a graphics card have an EVGA one. So the set of gamers with GPUs is not the same as the set of gamers with EVGA GPUs.

You can write this formally as:
$$
\exists g\in G:g\notin E
$$
*Translation: There exists an element $g$ in $G$ that is not in $E$. Aka, there exists a gamer who does not own an EVGA card.*

---
### Intervals

A set can be defined as an interval, like a range.

Use $[a,b]$ for an inclusive bound.

Use $(a,b)$ for an exclusive bound.

Use a combination of $[]$ and $()$ to have half open interval.

Examples would be:
- $[3,6]$ would be all real numbers between 3 and 6, including 3 and 6.
- $(3,6)$ would be all real numbers between 3 and 6, **not** including 3 and 6.
- $(3,6]$ would be all real numbers between 3 and 6, not including 3.
- $[3,6)$ would be all real numbers between 3 and 6, not including 3.

---
### Set Minus

$$
A\setminus B=\left\{a:a\in A,a\notin B\right\}
$$
This is just the set A without the elements that are in set B.

---
### Powerset of A

$$\begin{aligned}
\wp(A)=\left\{A':A\subseteq A\right\}
\end{aligned}$$
The powerset of A is the set of all subsets of A.

---
### Cartesian Product

$$\begin{aligned}
A\times B=\left\{(a,b):a\in A,b\in B\right\}
\end{aligned}$$

Example:
$$\begin{aligned}
\left\{2,3\right\}\times\left\{5,6\right\}=\left\{(2,5),(2,6),(3,5),(3,6)\right\}
\end{aligned}$$

It returns a set of **ordered** pairs with elements from A then elements of B.
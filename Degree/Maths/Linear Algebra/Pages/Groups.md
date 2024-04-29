---
tags:
  - degree/mathsforcs/linearalgebra
aliases:
  - Group
---
![[Linear Algebra MOC 🌍]]

### Groups 

The set $G$ is a group around the binary operation $\star$ if it satisfies some axioms.

>[!info] 
>A binary operation is one which takes two inputs to one output.

##### Closed

$\star$ must be closed on $G$. That means the output of the binary operation must also be in the set $G$. I.e. $\star : G \times G \rightarrow G$.

An example would be addition on integers. $2+3=5$. Since 2, 3 and 5 are integers, this would be closed.

Division would not be closed on integers since $\frac{5}{2}=2.5$. Since 2.5 is not an integer, this would not be closed.

##### Associative

$\star$ must be [[Associative]] on $G$. For all $a,b,c$ in $G$: $a \star (b \star c) \equiv (a \star b) \star c$.

An example would be multiplication of integers:
$$
2 \times (3 \times 4)=(2 \times 3) \times 4 = 24
$$

A non-associative action would be matrix multiplication.
$$
\begin{align*}
A&= \begin{bmatrix}
1 & 2\\
3 & 4
\end{bmatrix}\\
\\
B&= \begin{bmatrix}
4 & 3\\
2 & 1
\end{bmatrix}\\
\\
AB &= \begin{bmatrix}
8 & 5\\
20 & 13
\end{bmatrix}\\
\\
BA &= \begin{bmatrix}
13 & 20\\
5 & 8
\end{bmatrix}\\
\\
\therefore AB &\ne BA
\end{align*}
$$

##### Existence of an Identity Element

There exists an identity element $e \in G$ such that $\forall a \in G$, $a \star e = e \star a = a$.

The identity element of integer addition is $0$.
$$
2+0=2
$$
The identity element of multiplication is $1$.
$$
5\times 1 = 5
$$

##### Existence of an Inverse Operator 

$\star$ has an inverse operator such that $\forall a \in G$, $\exists b \in G$ such that $a\star b = b \star a = e$.

The inverse operator for integer addition is the negative numbers.
$$
2 + (-2) = 0
$$

The inverse operator of integer multiplication does not exist. An inverse operator is such that $2 \times b = 1$, $\therefore b=\frac{1}{2}$. But $\frac{1}{2}$ is not an integer and as such integer multiplication is not a group.
But real number multiplication would be a group as then $\frac{1}{2}$ would be a part of $G$.

---
### Finite Groups

The examples above all have infinite sets like $\mathbb{R}$ or $\mathbb{N}$.

In computer science, it's common to study finite sets like the bits $\{0,1\}$.

We can study $\mathbb{Z}_{n}$ modulo arithmetic, where the numbers wrap around.

The group table of $\mathbb{Z}_{4}$ with addition looks like this.

| + | 0 | 1 | 2 | 3 |
| :----: | :-: | :----: | :----: | :----: |
| **0** | 0 | 1 | 2 | 3 |
| **1** | 1 | 2 | 3 | 0 |
| **2** | 2 | 3 | 0 | 1 |
| **3** | 3 | 0 | 1 | 2 |
This even forms a group with only positive numbers as the inverse of 1 is 3. $\mod{(1+3)} = 0$.

---
### Additional Information

- [Groups on Wikipedia](https://en.wikipedia.org/wiki/Group_(mathematics))
- [[Maths for CS Linear Algebra Topic 1 Mathematical Structures#Groups|Steven Bradley's Notes on Groups]] [(GitHub Link)](https://github.com/stevenaeola/linalg_lectures/blob/main/1_structures/README.md#groups)
- [[Maths for CS Linear Algebra Week 2 Practical.pdf|Week 2 Practical Questions]]
- [[Maths for CS Linear Algebra Week 2 Practical Solutions.pdf|Week 2 Practical Solutions]]

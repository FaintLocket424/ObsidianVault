---
tags:
  - degree/mathsforcs/linearalgebra
aliases:
  - Field
---
![[Linear Algebra MOC 🌍]]

### Fields

A field is like a [[Groups|Group]] but it has the set $F$ and two binary operations on $F$ called addition $+$ and multiplication $\cdot$

---
### Field Axioms

##### Associativity

Both addition and multiplication must be [[Associative]].
$$
\begin{align*}
a + (b+c)&= (a+b)+c\\
a \cdot (b \cdot c) &= (a \cdot b) \cdot c
\end{align*}
$$

##### Commutativity

Both addition and multiplication must be [[Commutative]].
$$
\begin{align*}
a+b &= b+a\\
a \cdot b &= b \cdot a
\end{align*}
$$

##### Has Identity Element

The addition identity element $0$ and the multiplication element $1$ must exist in $F$.
$$
\begin{align*}
a+0 &= a\\
a \cdot 1 &= a
\end{align*}
$$

##### Additive Inverse

For every $a$ in $F$, there exists an element in $F$, denoted $-a$ such that $a+(-a)=0$.

##### Multiplicative Inverses

For every $a \ne 0$ in $F$, there exists an element in $F$, denoted $\frac{1}{a}$ or $a^{-1}$ such that $a \cdot \frac{1}{a} = 1$.

##### Distributivity

Multiplication is [[Distributive]] over addition.
$$
a \cdot (b + c) = (a \cdot b) + (a \cdot c)
$$
Distributive 

---
### Additional Information

- [Classic Definition of a Field on Wikipedia](https://en.wikipedia.org/wiki/Field_(mathematics)#Classic_definition)
- [[Maths for CS Linear Algebra Topic 1 Mathematical Structures#Structures (equipped) with multiple operations|Steven Bradley's Notes on Fields]] [(GitHub Link)](https://github.com/stevenaeola/linalg_lectures/blob/main/1_structures/README.md#structures-equipped-with-multiple-operations)
- [[Maths for CS Linear Algebra Week 2 Practical.pdf|Week 2 Practical Questions]]
- [[Maths for CS Linear Algebra Week 2 Practical Solutions.pdf|Week 2 Practical Solutions]]

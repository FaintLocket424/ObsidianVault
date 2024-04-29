---
tags:
  - degree/mathsforcs/linearalgebra
---
![[Linear Algebra MOC 🌍]]

### Vector Space 

- A vector space is a mathematical structure with sets, operations and axioms.
- It has two sets, the scalars $F$ and the [[Vectors]] $V$.
- $V$ is a [[Commutative]] [[Groups|Group]] with addition $\mathbf{u} + \mathbf{v} = \mathbf{v} + \mathbf{u}$.
- $F$ forms a field.
- And we have scalar multiplication : $F \times V \rightarrow V$.

---
### Vector Space Axioms

- $a(b \mathbf{v})=(ab)\mathbf{v}$
- $1\mathbf{v} = \mathbf{v}$
- $a(\mathbf{u} + \mathbf{v}) = a\mathbf{u} + a\mathbf{v}$
- $(a + b)\mathbf{v} = a\mathbf{v} + b\mathbf{v}$

---
### Basis of a Vector Space

A subset $S$ of the $V$ is a basis for $V$ if
- $S$ is a [[Linear Combinations#Spanning Set|Spanning Set]] and
- $S$ is [[Linear Combinations#Linear Dependence|Linearly Independent]]

The standard/canonical basis for $\mathbb{R}^{3}$ is $\lbrace (1,0,0), (0,1,0), (0,0,1) \rbrace$

These are known as $\hat{\imath}$, $\hat{\jmath}$ and $\hat{k}$. 

Any vector in $V$ can be written as a linear combination of a basis.
This is called the basis representation.

---
### Dimension of a Vector Space

The dimension refers to the cardinality of its basis.
For $\mathbb{R}^{3}$ it's 3.

---
### Complex Vector Space 

Similar to $\mathbb{R}^{n}$ but the vector space $\mathbb{C}^{n}$ consists of Complex Vectors.

Complex vectors have complex components.
$$
\vec{v} = 
\begin{bmatrix}
1+4i \\ -3i \\ 2
\end{bmatrix}
$$
We can also do some [[Operations of Complex Numbers|Complex Operations]] on complex vectors.
$$
\begin{align*}
\text{Re}(\vec{v}) &= \begin{bmatrix}
1 \\ 0 \\ 2
\end{bmatrix}\\
\\
\text{Im}(\vec{v}) &= \begin{bmatrix}
4\\
-3\\
0
\end{bmatrix}\\
\\
\overline{v} &= \begin{bmatrix}
1-4i\\
3i\\
2
\end{bmatrix}
\end{align*}
$$
There area also some complex number facts that apply to complex vectors.

For any vectors $\mathbf{u}, \mathbf{v} \in \mathbb{C}^{n}$ and a scalar $k \in \mathbb{C}$, the following hold:
- $\overline{\overline{\mathbf{u}}} = \mathbf{u}$
- $\overline{k \mathbf{u}} = \overline{k} \cdot \overline{\mathbf{u}}$
- $\overline{\mathbf{u} + \mathbf{v}} = \overline{\mathbf{u}} + \overline{\mathbf{v}}$
- $\overline{\mathbf{u} - \mathbf{v}} = \overline{\mathbf{u}} - \overline{\mathbf{v}}$



---
### Additional information

- [Vector Spaces on Wikipedia](https://en.wikipedia.org/wiki/Vector_space)
- [[Maths for CS Linear Algebra Topic 2 Vector Spaces and Linear Combinations#Vector space|Steven Bradley's Notes on Vector Space]] [(GitHub Link)](https://github.com/stevenaeola/linalg_lectures/blob/main/2_linear_combination/README.md#vector-space)
- [[Maths for CS Linear Algebra Week 4 Practical.pdf|Week 4 Practical Questions]]
- [[Maths for CS Linear Algebra Week 4 Practical Solutions.pdf|Week 4 Practical Solutions]]

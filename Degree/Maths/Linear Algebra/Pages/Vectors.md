---
tags:
  - degree/mathsforcs/linearalgebra
---
![[Linear Algebra MOC 🌍]]

### Notation

- Vectors are written in **bold** $\mathbf{u}, \mathbf{v}$.
- You can also do $\overline{v}, \underline{v}, \vec{v}$
- Scalars are written normally $a,b$.
- Vectors in $\mathbb{R}^{3}$ can be written as $(1,-2,0)$ or as column vectors
$$
\mathbf{v}=\begin{bmatrix}1 \\ -2 \\ 0\end{bmatrix}
$$

A vector is just an $n \times 1$ matrix.
$$
\begin{align*}
\boldsymbol{u} &= \begin{bmatrix}
1 \\ 2
\end{bmatrix} \in \mathbb{R}^{2}\\
\\
\boldsymbol{v} &= \begin{bmatrix}
1 \\ 2 \\ 3
\end{bmatrix} \in \mathbb{R}^{3}\\
\\
\boldsymbol{w} &= \begin{bmatrix}
1\\
2\\
3\\
4\\
5\\
6
\end{bmatrix} \in \mathbb{R}^{6}
\end{align*}
$$

---
### Vector Norms

##### Generalised Norms 

Given a vector space $X$, a function $d:X \to \mathbb{R}$ is a *norm* if it satisfies these properties:
- The triangle inequality: $d(\mathbf{x}+\mathbf{y}) \le d(\mathbf{x}) + d(\mathbf{y})$ $\forall \mathbf{x},\mathbf{y} \in X$
- Absolute homogeneity $d(s \mathbf{x}) = |s| d(\mathbf{x})$ $\forall \mathbf{x} \in X$ and scalars $s$.
- Positive definite. If $d(\mathbf{x})=0$, then $\mathbf{x}=0$.

##### Euclidian Norm

The Euclidean norm of the vector $\mathbf{x}$ is represented as $\| \mathbf{x} \|_{2}$ or just $\| \mathbf{x} \|$
$$
\| \mathbf{x} \|_{2} = \sqrt {\sum_{i} \left|x_{i}\right|^{2} } 
$$
This is the same as using the Pythagorean Theorem $l = \sqrt{x^{2} + y^{2}}$.

###### Example in $\mathbb{R}^{n}$
$$
\begin{align*}
\|(3,5,2)\|_{2} &= \sqrt{|3|^{2} + |5|^{2} + |2|^{2}}\\
&= \sqrt{9 + 25 + 4}\\
&= \sqrt{38}
\end{align*}
$$
###### Example in $\mathbb{C}^{n}$
$$
\begin{align*}
\|(3+i,1-2i,-2i)\|_{2} &= \sqrt{|3+i|^{2} + |1-2i|^{2} + |-2i|^{2}}\\
&= \sqrt{(\sqrt{10})^{2} + (\sqrt{5})^{2} + (\sqrt{4})^{2}}\\
&= \sqrt{10 + 5 + 4}\\
&= \sqrt{19}
\end{align*}
$$
##### Manhattan Norm

In Manhattan the streets are laid out in a grid.
So if you were looking for the distance between two places, the distance would be a north/south distance then the east/west distance.

This gives rise to the Manhattan distance
$$
d_{M}(\mathbf{x}) = \sum_{i} | x_{i} |
$$

##### p-norms

With a $p \in \mathbb{R}^{+}$ we define the p-norm $\ell_{p}$ as
$$
\| \mathbf{x} \|_{p} = \sqrt[p]{\sum_{i} | x_{i} |^{p}}
$$

Note that $\ell_{1}$ is the [[#Manhattan Norm]] and $\ell_{2}$ is [[#Euclidian Norm]].

If $p \to \infty$ then 
$$
\ell_{\infty} = \max (|x_{1}|, \ldots, |x_{n}|)
$$

And if $p \to 0$ then
$$
\ell_{0} = |x_{0}|^{0} + \ldots + |x_{n}|^{0}
$$
Which is also the number of components of $\mathbf{x}$ which are non-zero. This is the Hamming distance but is not a norm (Violates absolute homogeneity).


---
### Unit Vectors

A unit vector is a vector of length (norm) 1. It's represented by $\hat{x}$.
$$
\hat{\mathbf{x}} = \frac{\mathbf{x}}{\| \mathbf{x} \|}
$$

---
### Dot Product

Given vectors $\mathbf{a}$, $\mathbf{b}$ we define the dot product as
$$
\mathbf{a} \cdot \mathbf{b} = \| \mathbf{a} \| \| \mathbf{b} \| \cos \theta
$$
Where $\theta$ is the angle between $\mathbf{a}$ and $\mathbf{b}$.

The dot product has many properties:
- $\hat{\mathbf{a}} \cdot \hat{\mathbf{b}} = \cos \theta$
- $(s \mathbf{a}) \cdot \mathbf{b} = s(\mathbf{a} \cdot \mathbf{b})$
- $(\mathbf{a_1} + \mathbf{a_2})\cdot \mathbf{b} = \mathbf{a_1} \cdot \mathbf{b} + \mathbf{a_2} \cdot \mathbf{b}$
- $\mathbf{a} \cdot \mathbf{b} = 0$ if the vectors are orthogonal (90 degrees apart).
- $\mathbf{a} \cdot \mathbf{a} = \| \mathbf{a} \|^{2}$
- $\mathbf{u} \cdot \mathbf{v} = \mathbf{u}^{T} \mathbf{v} = \mathbf{v}^{T} \mathbf{u}$
- $\|\mathbf{u}\| = \mathbf{u} \cdot \mathbf{u} = \mathbf{u}^{T} \mathbf{u}$

To calculate the dot product of two vectors
$$
\mathbf{a} \cdot \mathbf{b} = \sum^{n}_{i=1} a_{i} b_{i}
$$
Example:
$$
\begin{bmatrix}
1 \\ 2 \\ 3
\end{bmatrix} \cdot 
\begin{bmatrix}
4 \\ 5 \\ 6
\end{bmatrix} = (1)(4) + (2)(5) + (3)(6) = 32
$$

---
### Complex Dot Product

If $\mathbf{u} = (u_{1},\ldots,u_{n})$ and $\mathbf{v} = (v_{1}, \ldots, v_{n}) \in \mathbb{C}^{n}$ then
$$
\mathbf{u} \cdot \mathbf{v} = u_{1} \overline{v_{1}} + \ldots + u_{n} \overline{v_{n}}
$$

Properties of the complex dot product
- $\mathbf{u} \cdot \overline{\mathbf{v}} = \mathbf{u}^{T} \mathbf{v} = \overline{\mathbf{v}}^{T} \mathbf{u}$
- $\|\mathbf{u}\| = \mathbf{u} \cdot \mathbf{u} = \mathbf{u}^{T} \overline{\mathbf{u}}$
- $\mathbf{u} \cdot (\mathbf{v} + \mathbf{w}) = \mathbf{u} \cdot \mathbf{v} + \mathbf{u} \cdot \mathbf{w}$
- $(k \mathbf{u}) \cdot \mathbf{v} = k(\mathbf{u} \cdot \mathbf{v})$ and $\mathbf{u} \cdot (k \mathbf{v}) = \overline{k} (\mathbf{u} \cdot \mathbf{v})$
- $\mathbf{v} \cdot \mathbf{v} \ge 0$

##### Example $\mathbf{u}=(1+i,i,3-i)$ and $v=(1+i,2,4i)$
$$
\begin{align*}
\mathbf{u} \cdot \mathbf{v} &= (1+i)(1-i) + (i)(2) + (3-i)(-4i) = -2-10i\\
\\
\mathbf{v} \cdot \mathbf{u} &= (1+i)(1-i)+(2)(-i) + (4i)(3+i) = -2+10i
\end{align*}
$$

---
### Orthonormality

Vectors are orthonormal if they are both orthogonal and normal.

It's useful to have orthonormal basis vectors.


---
### Additional Information

- [[Maths for CS Linear Algebra Topic 7 Norms and Dot Product|Steven Bradley's Notes on Norms and Dot Product]]

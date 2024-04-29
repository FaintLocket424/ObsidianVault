---
tags:
  - degree/mathsforcs/linearalgebra
---
![[Linear Algebra MOC 🌍]]

### Linear Maps

A Linear Map $f$ is a function which maps vectors in one vector space $V$ to another vector space $W$ over a field $F$ such that
$$
f:V \rightarrow W
$$
The function $f$ must also follow these rules to be a linear map:
$$
\begin{align*}
f(\mathbf{u}+\mathbf{v}) &= f(\mathbf{u}) + f(\mathbf{v})\\
\\
f(a \mathbf{v}) &= af(\mathbf{v})
\end{align*}
$$
One important property of linear maps is that they preserve the straight lines of the coordinate grid.

If $V=W$ then $f$ is an endomorphism.

---
### Linear Map Examples

- Scaling
- Reflection 
- Rotation 
- Shearing 
- Projection 
- Embedding 
- Differentiation (on polynomials)

---
### Linear Mapping on Basis Vectors

A vector can always be written as a linear combination of its [[Vector Space#Basis of a Vector Space|Basis Vectors]].
$$
\begin{align*}
\mathbf{v} &= \sum^{n}_{i=i} a_{i}v_{i}
\end{align*}
$$
So, because of the [[#Linear Maps|Rules of Linear Maps]], we can write
$$
\begin{align*}
f(\mathbf{v}) &= f\left(\sum^{n}_{i=i} a_{i}v_{i}\right) = \sum^{n}_{i=1} a_{i} f(s_{i})
\end{align*}
$$
So, a linear map is characterised by its effect on the basis vectors.

---
### Calculating from Basis Vector Images

To rotate $(2,3)$ $90 \degree$ anti-clockwise, we only need to know the image of the basis vectors.
$$
\begin{align*}
\mathbf{e}_{1} &\rightarrow \mathbf{e}_{2}\\
\mathbf{e}_{2} &\rightarrow -\mathbf{e_{1}}
\end{align*}
$$
With this we can say that the image of $(2,3)$ is
$$
2 \mathbf{e}_{2} + 3(- \mathbf{e}_{1}) = (-3,2)
$$

---
### Basis Images with Matrices

Basis vector images can be generalised under a matrix:
$$
\small{ A = \begin{pmatrix} a_{11} & a_{12} & a_{13} \\ a_{21} & a_{22} & a_{23}\\
a_{31} & a_{32} & a_{33}
\end{pmatrix}}
$$
Here the new basis vectors are $(a_{11},a_{21},a_{31})$, $(a_{12},a_{22},a_{32})$ and $(a_{13},a_{23},a_{33})$.

---
### Domain and Codomain of Transformations

Take the linear map $T$ for example:
$$
T=\begin{bmatrix}
1 & 2 & 3 \\ 4 & 5 & 6
\end{bmatrix}
$$
This $2 \times 3$ matrix maps $\mathbb{R}^{3}$ vectors to $\mathbb{R}^{2}$. E.g.
$$
T \begin{bmatrix}
2 \\ 3 \\ 1
\end{bmatrix} = \begin{bmatrix}
11 \\ 29
\end{bmatrix}
$$

---
### Identity Matrix

Using the [[Matrices#Identity Matrix|Identity Matrix]] as a linear map outputs the same vector as input.
$$
Ix=x
$$

---
### Combining Linear Maps 

Suppose we have two linear maps $f$ and $g$, represented by the matrices $A$ and $B$.

The linear map for $f \circ g$ will be $AB$.

This will apply $B$, then apply $A$. Remember that matrix multiplication is not [[Commutative]], so $AB \ne BA$.

---
### Determinants of Linear Maps

If we have a matrix $A$ representing the linear map $f$, the [[Matrices#Matrix Determinant|Determinant]] of $A$ is how much areas (In $\mathbb{R}^{2}$) are scaled by the transformation.

In $\mathbb{R}^{3}$, the determinant refers to how much volumes are scaled.

If the determinant is negative, this means space has been inverted, so $\hat{\jmath}$ is on the right hand side of $\hat{\imath}$ instead of the left like usual.

If the determinant is zero, then all areas are being squashed into a space with no area, be that a line or point.

---
### Null Space or Kernel

The null space or kernel is the set of vectors which map to $\mathbf{0}$.

The kernel itself forms a vector space of all linear combinations which map to $\mathbf{0}$.

The *nullity* of a matrix is the dimension of the kernel.
Given a linear map $T:V \to W$, then
$$
\text{rank} (T) + \text{nullity} (T) = \dim(V)
$$


---
### Additional Information

- [Linear Maps on Wikipedia](https://en.wikipedia.org/wiki/Linear_map)
- [3B1B Chapter 3: Linear transformations and matrices](https://www.youtube.com/watch?v=kYB8IZa5AuE&list=PLZHQObOWTQDPD3MizzM2xVFitgF8hE_ab&index=3) 
- [3B1B Chapter 4: Matrix multiplication as composition](https://www.youtube.com/watch?v=XkY2DOUCWMU&list=PLZHQObOWTQDPD3MizzM2xVFitgF8hE_ab&index=4)
- [[Maths for CS Linear Algebra Topic 3 Linear Maps|Steven Bradley's Notes on Linear Maps]] [(GitHub Link)](https://github.com/stevenaeola/linalg_lectures/blob/main/3_linear_maps/README.md)
- [[Maths for CS Linear Algebra Week 6 Practical.pdf|Week 6 Practical Questions]]
- [[Maths for CS Linear Algebra Week 6 Practical Solutions.pdf|Week 6 Practical Solutions]]

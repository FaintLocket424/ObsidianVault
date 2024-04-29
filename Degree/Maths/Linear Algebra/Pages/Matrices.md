---
tags:
  - degree/mathsforcs/linearalgebra
---
![[Linear Algebra MOC 🌍]]

### Matrix Size

An $m \times n$ matrix is $m$ rows tall by $n$ columns long.

$$
\begin{bmatrix}
6 & 5 & 6 \\ 3 & 2 & 1
\end{bmatrix}
$$
This is a $2\times3$ matrix.

---
### General Matrix

$$
A = \begin{bmatrix}
a_{11} & a_{12} & a_{13} & \cdots & a_{1n} \\ 
a_{21} & a_{22} & a_{23} & \cdots & a_{2n} \\ 
a_{31} & a_{32} & a_{33} & \cdots & a_{3n} \\ 
\vdots & \vdots & \vdots & \ddots & \vdots \\ 
a_{m1} & a_{m2} & a_{m3} & \cdots & a_{mn}
\end{bmatrix}
$$
---
### Matrix Transpose

A transpose means flipping a matrix over its diagonal.

![[Matrix_transpose.gif]]

The transpose of an $n \times m$ matrix will be an $m \times n$ matrix.

---
### Symmetric Matrices

A matrix is symmetrical if it is equal to its [[#Matrix Transpose|Transpose]].
$$
A = A^{T}
$$

Symmetrical $2 \times 2$ matrix
$$
\begin{bmatrix}
a & b \\ 
b & a
\end{bmatrix}
$$
Symmetrical $3 \times 3$ matrix
$$
\begin{bmatrix}
a & b & c \\ 
b & e & f \\ 
c & f & g
\end{bmatrix}
$$

---
### Matrix Similarity

Square matrices $A$ and $B$ are called similar if $A = P^{-1} B P$ for some $P$.

Note that if $A = P^{-1} B P$ then $B = P A P^{-1}$.

Similar matrices share many features like
- $A$ is invertible iff $B$ is invertible.
- Determinants 
- Trace 
- Rank 
- Nullity 
- Characteristic Polynomial 
- Eigenvalues 
- Dimensions of eigenspaces

Matrices $A$ and $B$ are similar iff they represent the same linear operator $f : \mathbb{R}^{n} \to \mathbb{R}^{n}$, possibly in different bases.

---
### Notation

We may just write $A=(a_{ij})$.

The entries in a matrix may be real numbers, complex numbers, polynomials (what) etc.

We write $\text{Mat}_{m \times n}(\mathbb{R})$ for the set of all real matrices of size $m\times n$.

If $m=n$, then we get a square matrix and we write $\text{Mat}_n(\mathbb{R})$.

---
### Identity Matrix 

The identity matrix is one which has 1 along the diagonal.
$$
I = \begin{bmatrix} 1 & 0 & \cdots & 0 \\ 0 & 1 & \cdots & 0\\
\vdots & \vdots & \ddots & \vdots \\0 & 0 & \cdots & 1
\end{bmatrix}
$$

---
### Matrix Multiplication 

Given matrix $A$ which is $m \times n$ and matrix $B$ which is $n \times k$, the output of $AB$ will be $m \times k$.
$$
\begin{pmatrix} 1 & -2 & 3 \\ -4 & 5 & -6 \end{pmatrix}
\begin{pmatrix} 9 \\ 8 \\ 7 \end{pmatrix} = 
\begin{pmatrix} 1 \times 9 -2 \times 8 + 3 \times 7 \\ -4 \times 9 +5 \times 8 -6 \times 7\end{pmatrix} =
\begin{pmatrix} 14 \\ -38\end{pmatrix}
$$

---
### Matrix Determinant

For a 2x2 matrix, the determinant is simple.
$$
\det\left(\begin{bmatrix}a & b \\ c & d\end{bmatrix}\right) = ad-bc
$$
For a 3x3 matrix, it's a bit more complex.
$$
\begin{align*}
\begin{vmatrix}
a & b & c \\ d & e & f \\ g & h & i
\end{vmatrix} = a &\begin{vmatrix}
e & f \\ h & i
\end{vmatrix}\\
- b &\begin{vmatrix}
d & f \\ g & i
\end{vmatrix}\\
\\
+ c &\begin{vmatrix}
d & e \\ g & h
\end{vmatrix}\\
\end{align*}
$$
The determinant is only a defined function for square matrices.

##### Determinant Properties
- If a matrix $A$ has a column of just zeros then $\det(A)=0$.
- If the matrix has linearly dependent columns then the determinant will be 0.
- $\det(AB) = \det(A) \cdot \det(B)$
- $\det(A^{-1}) = \frac{1}{\det(A)}$

##### Determinant of a Diagonal Matrix

$$
\begin{align*}
\begin{vmatrix}
a & 0 & 0 \\ 0 & b & 0 \\ 0 & 0 & c
\end{vmatrix} &= abc \begin{vmatrix}
1 & 0 & 0\\
0 & 1 & 0\\
0 & 0 & 1
\end{vmatrix}\\
\\
&= abc
\end{align*}
$$

---
### Matrix Inverses

Suppose we want to find the inverse of
$$
\begin{bmatrix}
1 & 2 \\ 3 & 4
\end{bmatrix}
$$
Then we want to find
$$
\begin{bmatrix}
w & x \\ y & z
\end{bmatrix}
\begin{bmatrix}
1 & 2 \\ 3 & 4
\end{bmatrix} = 
\begin{bmatrix}
1 & 0 \\ 0 & 1
\end{bmatrix}
$$
This provides these equations
$$
\begin{align*}
w + 3x &= 1\\
2w + 4x &= 0\\
y + 3z &= 0\\
2y+4z &= 1
\end{align*}
$$
Solving these equations for $w$, $x$, $y$ and $z$, the inverse is
$$
\begin{bmatrix}
-2 & 1 \\ \frac{3}{2} & - \frac{1}{2}
\end{bmatrix}
$$
Matrix inverses only exist for square matrices.

---
### Matrix Column Space 

The set of all possible outputs of $A\mathbf{v}$ is the column space of $A$.

Given a linear transformation $f: X \to Y$, this makes $f(X)$ the column space.

With a linear map, the columns show where the basis vectors end up.
$$
\begin{bmatrix}
2 & -2 \\ 1 & -1
\end{bmatrix}
$$
So here $f(\hat{\imath})=\begin{bmatrix}2 \\ 1\end{bmatrix}$ and $f(\hat{\jmath})=\begin{bmatrix}-2 \\ -1\end{bmatrix}$.

And the span of this linear combination $af(\hat{\imath})+bf(\hat{\jmath})$ is the column space.

---
### Matrix Column Rank

Column rank is the number of dimensions in the [[#Matrix Column Space|Column Space]].
The column rank will equal the number of [[Linear Combinations#Linear Dependence|Linearly Independent]] columns.

Rank 1: All vectors transformed by the matrix end on a 1D line.
Rank 2: All vectors transformed by the matrix end on a 2D plane.
Rank 3: All vectors transformed by the matrix end in a 3D cube.

If the column rank equals the number of columns, then it's a Full Rank matrix.

With a matrix in [[Gaussian Elimination#Row Echelon Form (ref)|Row-Echelon Form]], the number of non-zero rows equals the matrix rank.
$$
A=\begin{bmatrix}
1 & 2 & 0 & 3 & 0 & 7 \\ 
0 & 0 & 1 & 0 & 0 & 1 \\ 
0 & 0 & 0 & 0 & 1 & 2
\end{bmatrix}
$$
So $\text{rank}(A)$ is 3

---
### Matrix Row Rank

Row rank == Column Rank

---
### Diagonal Matrices

A diagonal matrix is a matrix which only has items on the diagonal.
$$
A = \begin{bmatrix}
a & 0 & 0 \\ 
0 & b & 0 \\ 
0 & 0 & c
\end{bmatrix}
$$

The shorthand is $D = \text{diag}(\lambda_{1},\ldots,\lambda_{n})$
$$
D = \begin{bmatrix}
\lambda_{1} & 0 & \cdots & 0 \\ 
0 & \lambda_{2} & \cdots & 0 \\ 
\vdots & \vdots & \ddots & \vdots \\ 
0 & 0 & \cdots & \lambda_{n}
\end{bmatrix}
$$

##### Diagonalisable
A matrix $A$ is called diagonalisable if it's similar to a diagonal matrix.

In other words, if there exists $P$ such that $P^{-1}AP$ is diagonal. $P$ is said to diagonalise $A$.

$A$ is also diagonalisable if it decomposes as $A=PDP^{-1}$ and $D$ is diagonal.

An $n \times n$ matrix is diagonalisable iff it has $n$ linearly independent eigenvectors.

---
### Complex Matrices 

A complex matrix is one which has components in $\mathbb{C}$.

Take the complex matrix $A$
$$
A = \begin{bmatrix}
1+2i & 3 - 2i & 3 \\ 
3 & -2i & 1 \\ 
2i & 2+3i & -1
\end{bmatrix}
$$
We can take [[Operations of Complex Numbers#$Re(z)$ and $Im(z)$|Re(A)]], [[Operations of Complex Numbers#$Re(z)$ and $Im(z)$|Im(A)]] and the [[Complex Conjugate|Conjugate]] of $A$ 
$$
\begin{align*}
\text{Re}(A) &= \begin{bmatrix}
1 & 3 & 3\\
3 & 0 & 1\\
0 & 2 & -1
\end{bmatrix}\\
\\
\text{Im}(A) &= \begin{bmatrix}
2 & -2 & 0\\
0 & -2 & 0\\
2 & 3 & 0
\end{bmatrix}\\
\\
\overline{A} &= \begin{bmatrix}
1-2i & 3+2i & 3\\
3 & 2i & 1\\
-2i & 2-3i & -1
\end{bmatrix}
\end{align*}
$$
We also have other properties of complex matrices.
- $\overline{\overline{A}} = A$
- $\overline{A^{T}} = (\overline{A})^{T}$
- $\overline{AB} = \overline{A} \cdot \overline{B}$


---
### Additional Information

- [Rank on Wikipedia](https://en.wikipedia.org/wiki/Rank_(linear_algebra))

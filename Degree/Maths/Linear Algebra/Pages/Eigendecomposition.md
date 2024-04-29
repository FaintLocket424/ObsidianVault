---
tags:
  - degree/mathsforcs/linearalgebra
---
![[Linear Algebra MOC 🌍]]

### Eigendecomposition

The process of a matrix $A$ being decomposed into the form $PDP^{-1}$.

$P$ is the eigenvectors
$D$ is a diagonal matrix eigenvalues.
$$
D = \begin{bmatrix}
\lambda_{1} & 0 & 0 \\ 
0 & \lambda_{2} & 0 \\ 
0 & 0 & \lambda_{3}
\end{bmatrix}
$$

The $PDP^{-1}$ form allows for faster self-matrix multiplication.
$$
A^{k} = PD^{k}P^{-1}
$$
where
$$
D^{k} = \begin{bmatrix}
\lambda_{1}^{k} & 0 & 0 \\ 
0 & \lambda_{2}^{k} & 0 \\ 
0 & 0 & \lambda_{3}^{k}
\end{bmatrix}
$$

It's also useful for PCA.

---
### Algorithm for Diagonalisation

Given an $n \times n$ matrix $A$:
1. Find the eigenvalues of $A$
2. Find a basis in each eigenspace of $A$ and merge these basis into one set $S$.
3. If $S$ has fewer than $n$ vectors then $A$ is not diagonalisable.
4. Form the matrix $P=\begin{bmatrix}\mathbf{p}_{1}|\ldots|\mathbf{p}_{n}\end{bmatrix}$ where $S = \begin{Bmatrix}\mathbf{p}_{1},\ldots,\mathbf{p}_{n}\end{Bmatrix}$.
5. The matrix $D = P^{-1}AP$ is diagonal, where $D=\text{diag}(\lambda_{1},\ldots,\lambda_{n})$ where $\lambda_{i}$ is the eigenvalue corresponding to $\mathbf{p}_{i}$.

##### Example:
For $k \ne 0$, is the following matrix diagonalisable?
$$
A = \begin{bmatrix}
1 & k \\ 0 & 1
\end{bmatrix}
$$
First compute the characteristic polynomial $(\lambda-1)^{2}$.
So this has one eigenvalue $\lambda_{1}=1$.

The corresponding eigenspace is the [[Linear Maps#Null Space or Kernel|Null Space]] of
$$A-\lambda_{1}I=\begin{bmatrix}0 & -k \\ 0 & 0\end{bmatrix}$$
Since this doesn't have two linearly independent vectors, it is not diagonalisable.

---
### Eigendecomposition 

Let $A$ be a [[Matrices#Diagonalisable|Diagonalisable]] matrix.
We have $AP = PD$ where $P$ is invertible and its columns $\mathbf{p}_{1},\ldots,\mathbf{p}_{n}$ are eigenvectors of $A$. And $D=\text{diag}(\lambda_{1}, \ldots, \lambda_{n})$ and each $\lambda_{i}$ is the eigenvalue of $A$ corresponding to $\mathbf{p}_{i}$.

Then we have a decomposition $A = PDP^{-1}$.
Since the factors in this decomposition are made of eigenvectors and eigenvalues, it is called an Eigendecomposition of $A$.

##### Example

Find the Eigendecomposition of $A$ if one exists.
$$
A = \begin{bmatrix}
-2 & 0 & 3 \\ 
-8 & 2 & 8 \\ 
0 & 0 & 1
\end{bmatrix}
$$
First, we find the eigenvalues 
$$
\begin{align*}
\lambda_{1} &= -2\\
\lambda_{2} &= 2\\
\lambda_{3} &= 1
\end{align*}
$$
Then, find the eigenvectors
$$
\begin{align*}
\mathbf{v}_{1} &= (1,2,0)\\
\mathbf{v}_{2} &= (0,1,0)\\
\mathbf{v}_{3} &= (1,0,1)
\end{align*}
$$
Therefore 
$$
\begin{align*}
D &= \begin{bmatrix}
-2 & 0 & 0 \\ 
0 & 2 & 0 \\ 
0 & 0 & 1
\end{bmatrix}\\
\\
P &= \begin{bmatrix}
1 & 0 & 1\\
2 & 1 & 0\\
0 & 0 & 1
\end{bmatrix}
\end{align*}
$$
Then, invert $P$
$$
P^{-1} = \begin{bmatrix}
1 & 0 & -1 \\ 
-2 & 1 & 2 \\ 
0 & 0 & 1
\end{bmatrix}
$$
Giving
$$
\begin{bmatrix}
-2 & 0 & 3 \\ 
-8 & 2 & 8 \\ 
0 & 0 & 1
\end{bmatrix} = 
\begin{bmatrix}
1 & 0 & 1 \\ 
2 & 1 & 0 \\ 
0 & 0 & 1
\end{bmatrix}
\begin{bmatrix}
-2 & 0 & 0 \\ 
0 & 2 & 0 \\ 
0 & 0 & 1
\end{bmatrix}
\begin{bmatrix}
1 & 0 & -1 \\ 
-2 & 1 & 2 \\ 
0 & 0 & 1
\end{bmatrix}
$$


---
### Additional Information

- [Wikipedia]
- [[Maths for CS Linear Algebra Topic 13 Diagonalization.pdf]]
- [Maybe Practical Q and As]

---
tags:
  - degree/mathsforcs/linearalgebra
aliases:
  - PLU Decomposition
---
![[Linear Algebra MOC 🌍]]

### LU Decomposition 

LU Decomposition is the process of representing a square matrix $A$ as a product of two matrices.
$$
A = LU
$$
$L$ is the lower triangular and $U$ is the upper triangular.
$$
A = \begin{bmatrix}
2 & 6 & 2 \\ -3 & -8 & 0 \\ 4 & 9 & 2
\end{bmatrix} = 
\begin{bmatrix}
2 & 0 & 0 \\ -3 & 1 & 0 \\ 4 & -3 & 7
\end{bmatrix}
\begin{bmatrix}
1 & 3 & 1 \\ 0 & 1 & 3 \\ 0 & 0 & 1
\end{bmatrix} = LU
$$

---
### LU Requirements

To solve $A \mathbf{x} = \mathbf{b}$ via LU, some requirements must be met:
- Matrix $A$ must be square.
- You must not make any row exchanges.

---
### Calculating $L$ and $U$

Take this matrix
$$
B = \begin{bmatrix}
1 & 1 & -1 \\ 
1 & -2 & 3 \\ 
2 & 3 & 1
\end{bmatrix}
$$
The decomposition process is very similar to [[Gaussian Elimination]].

First we need to set up $L$ and $U$
$$
\begin{align*}
U &= \begin{bmatrix}
1 & 1 & -1 \\ 
1 & -2 & 3 \\ 
2 & 3 & 1
\end{bmatrix}\\
\\
L &= \begin{bmatrix}
1 & 0 & 0\\
& 1 & 0\\
&& 1
\end{bmatrix}
\end{align*}
$$

We now do Gaussian Elimination on the matrix $U$, keeping track of our row multipliers.

First we add $(-1)(R_{1})$ to $R_{2}$ to get a leading zero.
And the corresponding position in $U$ is the opposite of our multiplier, so $1$.
$$
\begin{align*}
U &= \begin{bmatrix}
1 & 1 & -1 \\ 
0 & -3 & 4 \\ 
2 & 3 & 1
\end{bmatrix}\\
\\
L &= \begin{bmatrix}
1 & 0 & 0\\
1 & 1 & 0\\
 & & 1
\end{bmatrix}
\end{align*}
$$

Next we add $(-2)R_{1}$ to $R_{3}$ to get a leading zero there.
And this makes the corresponding number in $U$ be $2$.
$$
\begin{align*}
U &= \begin{bmatrix}
1 & 1 & -1 \\ 
0 & -3 & 4 \\ 
0 & 1 & 3
\end{bmatrix}\\
\\
L &= \begin{bmatrix}
1 & 0 & 0\\
1 & 1 & 0\\
2 & & 1
\end{bmatrix}
\end{align*}
$$

Next we add $\left(\frac{1}{3}\right)R_{2}$ to $R_{3}$ to get a zero in row 3.
$$
\begin{align*}
U &= \begin{bmatrix}
1 & 1 & -1 \\ 
0 & -3 & 4 \\ 
0 & 0 & \frac{13}{3}
\end{bmatrix}\\
\\
L &= \begin{bmatrix}
1 & 0 & 0\\
1 & 1 & 0\\
2 & - \frac{1}{3} & 1
\end{bmatrix}
\end{align*}
$$

And so now we know that
$$
\begin{bmatrix}
1 & 1 & -1 \\ 
1 & -2 & 3 \\ 
2 & 3 & 1
\end{bmatrix} = 
\begin{bmatrix}
1 & 0 & 0\\
1 & 1 & 0\\
2 & - \frac{1}{3} & 1
\end{bmatrix}
\begin{bmatrix}
1 & 1 & -1 \\ 
0 & -3 & 4 \\ 
0 & 0 & \frac{13}{3}
\end{bmatrix}
$$

---
### PLU Decomposition

You cannot do LU decomposition if row exchanges need to be used.
This can be overcome using permutation matrices.

A permutation matrix is a square matrix obtained by interchanging rows in $I$.
$$
P = 
\begin{bmatrix}
0 & 0 & 0 & 1 \\ 
0 & 1 & 0 & 0 \\ 
1 & 0 & 0 & 0 \\ 
0 & 0 & 1 & 0
\end{bmatrix}
$$
If $P$ has size $n \times n$, then for any $n \times m$ matrix $A$, the product $PA$ is the matrix obtained from $A$ by permutating its rows in the same way as $P$ from $I$.

Note that $P^{-1} = P^{T}$ which makes $P^{-1}$ invertible.

So a PLU decomposition is representing a square matrix as $A = PLU$.

Since $P^{T}$ is invertible, $A \mathbf{x} = \mathbf{b}$ has the same solutions as $P^{T} A \mathbf{x} = P^{T} \mathbf{b}$. You then compute $\mathbf{b}' = P^{T} \mathbf{b}$ and write the system as $LU \mathbf{x} = \mathbf{b}'$ and solve.

---
### Additional Information

- [Wikipedia]
- [Lecture Notes]
- [Maybe Practical Q and As]

---
tags:
  - degree/mathsforcs/linearalgebra
---
![[Linear Algebra MOC 🌍]]

### Linear Systems

A linear system
$$
\begin{align*}
a_{11}x_{1} + a_{12}x_{2} + \ldots + a_{1n}x_{n} &= b_{1}\\
a_{21}x_{1} + a_{22}x_{2} + \ldots + a_{2n}x_{n} &= b_{2}\\
\vdots &= \vdots\\
a_{m1}x_{1} + a_{m2}x_{2} + \ldots + a_{mn}x_{n} &= b_{m}
\end{align*}
$$
Can be written as a matrix $A\boldsymbol{x}=\boldsymbol{b}$ where
$$
A=\begin{bmatrix}
a_{11} & a_{12} & \cdots & a_{1n} \\ 
a_{21} & a_{22} & \cdots & a_{2n} \\ 
\vdots & \vdots & \ddots & \vdots \\ 
a_{m1} & a_{m2} & \cdots & a_{mn}
\end{bmatrix},\quad \boldsymbol{x}=\begin{bmatrix}
x_{1} \\ x_{2} \\ \vdots \\ x_{n}
\end{bmatrix} \quad \text{and } \boldsymbol{b}=\begin{bmatrix}
b_{1} \\ b_{2} \\ \vdots \\ b_{m}
\end{bmatrix}
$$
$A$ is called the coefficient matrix.

If $A$ is square and invertible then the solution can be found as $\boldsymbol{x}=A^{-1}\boldsymbol{b}$.

---
### Solving Linear Systems Using Gauss-Jordan Elimination

$$
\begin{align*}
-2x_{3} + 7x_{5} &= 12\\
2x_{1} + 4x_{2} - 10x_{3} + 6x_{4} + 12x_{5} &= 28\\
2x_{1} + 4x^{2} - 5x_{3} + 6x_{4} - 5x_{5} &= -1
\end{align*}
$$
We can create a coefficient matrix from this system
$$
\begin{bmatrix}
\begin{array}{ccccc|c}
0 & 0 & -2 & 0 & 7 & 12 \\ 
2 & 4 & -10 & 6 & 12 & 28 \\ 
2 & 4 & -5 & 6 & -5 & -1
\end{array}
\end{bmatrix}
$$
Using [[Gaussian Elimination#Gauss-Jordan Elimination|Gauss-Jordan Elimination]] on this, we get
$$
\begin{bmatrix}
\begin{array}{ccccc|c}
1 & 2 & 0 & 3 & 0 & 7 \\ 
0 & 0 & 1 & 0 & 0 & 1 \\ 
0 & 0 & 0 & 0 & 1 & 2
\end{array}
\end{bmatrix}
$$
We can see the solution to this system is
$$
\begin{align*}
x_{1} &= -2x_{2} - 3x_{4} + 7\\
x_{3} &= 1\\
x_{5} &= 2
\end{align*}
$$

---
### Solving Linear Systems with LU Decomposition

Given the system of equations
$$
\begin{align*}
x_{1} + x_{2} - x_{3} &= 4\\
x_{1} - 2x_{2} + 3x_{3} &= -6\\
2x_{1} + 3x_{2} + x_{3} &= 7
\end{align*}
$$
We can write it as a matrix equation $A \mathbf{x} = \mathbf{b}$.
$$
\begin{bmatrix}
1 & 1 & -1 \\ 
1 & -2 & 3 \\ 
2 & 3 & 1
\end{bmatrix}
\begin{bmatrix}
x_{1} \\ x_{2} \\ x_{3}
\end{bmatrix} = 
\begin{bmatrix}
4 \\ -6 \\ 7
\end{bmatrix}
$$

Using [[LU Decomposition]], we can rewrite the coefficient matrix as two matrices $LU \mathbf{x} = \mathbf{b}$.
$$
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
\begin{bmatrix}
x_{1} \\ x_{2} \\ x_{3}
\end{bmatrix} = 
\begin{bmatrix}
4 \\ -6 \\ 7
\end{bmatrix}
$$

To solve, we first let $U \mathbf{x} = \mathbf{y}$. Then, $L \mathbf{y} = \mathbf{b}$.
We first solve $L \mathbf{y} = \mathbf{b}$ for $\mathbf{y}$ and then solve $U \mathbf{x} = \mathbf{y}$ for $\mathbf{x}$.
$$
\begin{bmatrix}
1 & 0 & 0 \\ 
1 & 1 & 0 \\ 
2 & - \frac{1}{3} & 1
\end{bmatrix}
\begin{bmatrix}
y_{1} \\ y_{2} \\ y_{3}
\end{bmatrix} = 
\begin{bmatrix}
4 \\ -6 \\ 7
\end{bmatrix}
$$
This gives the system
$$
\begin{align*}
y_{1} &= 4\\
y_{1} + y_{2} &= -6\\
2y_{1} - \frac{1}{3}y_{2} + y_{3} &= 7
\end{align*}
$$
which is very easy to solve.
$$
\begin{align*}
y_{1} &= 4\\
y_{2} &= -6 - 4 = -10\\
y_{3} &= 7 - 2(4) + \frac{1}{3}(-10) = - \frac{13}{3}
\end{align*}
$$
We now know that
$$
\mathbf{y} = \begin{bmatrix}
4 \\ -10 \\ - \frac{13}{3}
\end{bmatrix}
$$

Solving $U \mathbf{x} = \mathbf{y}$ 
$$
\begin{bmatrix}
1 & 1 & -1 \\ 
0 & -3 & 4 \\ 
0 & 0 & \frac{13}{3}
\end{bmatrix}
\begin{bmatrix}
x_{1} \\ x_{2} \\ x_{3}
\end{bmatrix} = 
\begin{bmatrix}
4 \\ -10 \\ - \frac{13}{3}
\end{bmatrix}
$$
This gives the equations (Written bottom to top)
$$
\begin{align*}
\frac{13}{3} x_{3} &= -\frac{13}{3}\\
-3x_{2} + 4x_{3} &= -10\\
x_{1} + x_{2} - x_{3} &= 4
\end{align*}
$$
And this can easily be solved
$$
\begin{align*}
x_{3} &= -1\\
x_{2} &= \frac{-10 - 4(-1)}{-3} = 2\\
x_{1} &= 4 - (2) + (-1) = 1
\end{align*}
$$




---
### Additional Information

- [[Maths for CS Linear Algebra Topic 5 Linear Equations and Gaussian Elimination.pdf|Steven Bradley's Notes on Solving Linear Systems with Gauss-Jordan Elimination]]

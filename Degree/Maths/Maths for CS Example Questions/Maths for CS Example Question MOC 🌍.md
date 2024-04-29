---
tags:
  - MOC
  - degree/mathsforcs
---
Up: [[Maths For CS MOC 🌍]]

### Question 1
##### Part a
I would use SVD decomposition to aid me. SVD is good for reducing the rank of a matrix and reducing its size from $m \times n$ values to 

##### Part b 
I would use Eigendecomposition on the transition matrix to get it in $P D P^{-1}$ form. I would then multiply this by the initial state matrix $A$ to get $P D P^{-1} A$. This is then useful because to do $k=100$ steps, we simply have to do $P D^{k} P^{-1} A$ and since $D$ is diagonal, it's very quick to do self-multiplication.

##### Part c 

### Question 2 
##### Part a 
###### Part ii
$$
\begin{align*}
A &= \begin{pmatrix}
1 & 0 & 0 \\ 
5 & 2 & 4 \\ 
4 & 2 & 1
\end{pmatrix}\\
\\
U &= \begin{pmatrix}
1 & 0 & 0\\
5 & 2 & 4\\
4 & 2 & 1
\end{pmatrix}\\
\\
L &= \begin{pmatrix}
1 & 0 & 0\\
  & 1 & 0\\
  &   & 1
\end{pmatrix}
\end{align*}
$$
Eigendecomposition of $U$:
$R_{2} = -5(R_{1}) + R_{2}$
$R_{3} = -4(R_{1}) + R_{3}$
$$
\begin{align*}
U &= \begin{pmatrix}
1 & 0 & 0 \\ 
0 & 2 & 4 \\ 
0 & 2 & 1
\end{pmatrix}\\
\\
L &= \begin{pmatrix}
1 & 0 & 0\\
5 & 1 & 0\\
4 &   & 1
\end{pmatrix}
\end{align*}
$$
$R_{3} = -1(R_{2}) + R_{3}$
$$
\begin{align*}
U &= \begin{pmatrix}
1 & 0 & 0\\
0 & 2 & 4\\
0 & 0 & -3
\end{pmatrix}\\
\\
L &= \begin{pmatrix}
1 & 0 & 0\\
5 & 1 & 0\\
4 & 1 & 1
\end{pmatrix}
\end{align*}
$$

###### Part ii 
If $Ax = b$, then $LUx = b$.

Let $Ux = y$ and $Ly = b$

$$
\begin{pmatrix}
1 & 0 & 0 \\ 
5 & 1 & 0 \\ 
4 & 1 & 1
\end{pmatrix} \begin{pmatrix}
y_{1} \\ y_{2} \\ y_{3}
\end{pmatrix} = \begin{pmatrix}
1 \\ 27 \\ 14
\end{pmatrix}
$$
Solve for $y$
$$
\begin{align*}
y_{1} &= 1\\
y_{2} &= 27 - 5(y_{1}) = 22\\
y_{3} &= 14 - 4(y_{1}) - 1(y_{2}) = -12
\end{align*}
$$
$$
y = \begin{pmatrix}
1 \\ 22 \\ -12
\end{pmatrix}
$$
Solving $Ux = y$
$$
\begin{pmatrix}
1 & 0 & 0 \\ 
0 & 2 & 4 \\ 
0 & 0 & -3
\end{pmatrix}
\begin{pmatrix}
x_{1} \\ x_{2} \\ x_{3}
\end{pmatrix}
= 
\begin{pmatrix}
1 \\ 22 \\ -12
\end{pmatrix}
$$
$$
\begin{align*}
x_{1} &= 1\\
x_{2} &= \frac{22 - 4(x_{3})}{2} = 3 \\
x_{3} &= 4
\end{align*}
$$
##### Part b 
$$
A = \begin{pmatrix}
2 & 2 \\ 
2 & 2 \\ 
2 & 1 \\ 
2 & 1
\end{pmatrix}
$$
$A = \begin{pmatrix}u_{1} | u_{2}\end{pmatrix}$
$Q = \begin{pmatrix}q_{1} | q_{2}\end{pmatrix}$
$$
v_{1} = u_{1}
$$
$$
\begin{align*}
v_{2} &= u_{2} - \frac{\langle u_{2}, v_{1} \rangle}{\|v_{1}\|^{2}} v_{1}\\
\end{align*}
$$
$\langle u_{2}, v_{1} \rangle = (2 \times 2) + (2 \times 2) + (2 \times 1) + (2 \times 1) = 12$
$\| v_{1} \|^{2} = 2^{2} + 2^{2} + 2^{2} + 2^{2} = 16$
$$
\begin{align*}
v_{2} &= \begin{pmatrix}
2 \\ 2 \\ 1 \\ 1
\end{pmatrix} - \frac{12}{16}\begin{pmatrix}
2 \\ 2 \\ 2 \\ 2
\end{pmatrix}\\
\\
v_{2} &= \begin{pmatrix}
\frac{1}{2}\\
\frac{1}{2}\\
- \frac{1}{2}\\
- \frac{1}{2}
\end{pmatrix}
\end{align*}
$$

$$
\begin{align*}
q_{1} &= \frac{1}{\|v_{1}\|}v_{1}\\
\\
q_{2} &= \frac{1}{\| v_{2} \|} v_{2}
\end{align*}
$$

$$
\begin{align*}
q_{1} &= \begin{pmatrix}
\frac{1}{2}\\
\frac{1}{2}\\
\frac{1}{2}\\
\frac{1}{2}
\end{pmatrix}\\
\\
q_{2} &= \begin{pmatrix}
\frac{1}{2}\\
\frac{1}{2}\\
- \frac{1}{2}\\
- \frac{1}{2}
\end{pmatrix}\\
\\
Q &= \begin{pmatrix}
\frac{1}{2} & \frac{1}{2}\\
\frac{1}{2} & \frac{1}{2}\\
\frac{1}{2} & - \frac{1}{2}\\
\frac{1}{2} & - \frac{1}{2}
\end{pmatrix}
\end{align*}
$$

$$
R = \begin{pmatrix}
\langle u_{1}, q_{1} \rangle & \langle u_{2}, q_{1} \rangle \\ 
\langle u_{1}, q_{2} \rangle & \langle u_{2}, q_{2} \rangle
\end{pmatrix}
$$
$$
\begin{align*}
\langle u_{1}, q_{1} \rangle &= 4\\
\langle u_{2}, q_{1} \rangle &= 3\\
\langle u_{1}, q_{2} \rangle &= 0\\
\langle u_{2}, q_{2} \rangle &= 1
\end{align*}
$$
$$
R = \begin{pmatrix}
4 & 3 \\ 0 & 1
\end{pmatrix}
$$
$$
A = QR = \begin{pmatrix}
\frac{1}{2} & \frac{1}{2} \\ 
\frac{1}{2} & \frac{1}{2} \\ 
\frac{1}{2} & - \frac{1}{2} \\ 
\frac{1}{2} & - \frac{1}{2}
\end{pmatrix} \begin{pmatrix}
4 & 3 \\ 0 & 1
\end{pmatrix}
$$
##### Part c
$$
A = \begin{pmatrix}
1 & 2 & 1 \\ 
2 & 1 & 1 \\ 
0 & 3 & 1
\end{pmatrix}
$$
The characteristic equation of $A$ is $\det (A - I \lambda) = 0$
$$
\begin{vmatrix}
1-\lambda & 2 & 1 \\ 
2 & 1-\lambda & 1 \\ 
0 & 3-\lambda & 1
\end{vmatrix} = 0
$$

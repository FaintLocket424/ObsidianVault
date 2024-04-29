---
tags:
  - incomplete
  - degree/mathsforcs/linearalgebra
---
![[Linear Algebra MOC 🌍]]

### How to
Find the QR Decomposition of $A$
$$
A = \begin{pmatrix}
2 & 2 \\ 
2 & 2 \\ 
2 & 1 \\ 
2 & 1
\end{pmatrix}
$$
Split $A$ into its column vectors $A = \begin{pmatrix}\mathbf{u}_{1} | \mathbf{u}_{2}\end{pmatrix}$
$$
\begin{align*}
\mathbf{u}_{1} &= \begin{pmatrix}
2\\
2\\
2\\
2
\end{pmatrix}\\
\\
\mathbf{u}_{2} &= \begin{pmatrix}
2\\
2\\
1\\
1
\end{pmatrix}
\end{align*}
$$
Now find $\mathbf{v}_{1}$ and $\mathbf{v}_{2}$ using the [[Orthonormal Sets#Gram-Schmidt Orthogonalisation Process|Gram-Schmidt Orthogonalisation Process]].
$$
\begin{align*}
\mathbf{v}_{1} &= \mathbf{u}_{1}\\
\\
\mathbf{v}_{2} &= \mathbf{u}_{2} - \frac{\langle \mathbf{u}_{2}, \mathbf{v}_{1} \rangle}{\| \mathbf{v}_{1} \|^{2}} \mathbf{v}_{1}
\end{align*}
$$
If you have more than two columns, look at [[Orthonormal Sets#Step 3|Step 3]] of the Gram-Schmidt process.

Now to get $\mathbf{q}$ we have to normalise $\mathbf{v}$.
$$
\begin{align*}
\mathbf{q}_{1} &= \frac{1}{\|\mathbf{v}_{1}\|} \mathbf{v}_{1}\\
\\
\mathbf{q}_{2} &= \frac{1}{\| \mathbf{v}_{2} \|} \mathbf{v}_{2}
\end{align*}
$$
And finding these values gets us
$$
\begin{align*}
\mathbf{q}_{1} &= \begin{pmatrix}
\frac{1}{2} \\ \frac{1}{2} \\ \frac{1}{2} \\ \frac{1}{2}
\end{pmatrix}\\
\\
\mathbf{q}_{2} &= \begin{pmatrix}
\frac{1}{2}\\
\frac{1}{2}\\
- \frac{1}{2}\\
- \frac{1}{2}
\end{pmatrix}
\end{align*}
$$
And so our $Q$ matrix is
$$
Q = \begin{pmatrix}
\frac{1}{2} & \frac{1}{2}\\
\frac{1}{2} & \frac{1}{2}\\
\frac{1}{2} & - \frac{1}{2}\\
\frac{1}{2} & - \frac{1}{2}
\end{pmatrix}
$$
And now we need the $R$ matrix which is made up of [[Inner Product|Inner Product]]
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


---
### Additional Information

- [Wikipedia]
- [Lecture Notes]
- [Maybe Practical Q and As]

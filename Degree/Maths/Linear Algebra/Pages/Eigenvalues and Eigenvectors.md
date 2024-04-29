---
tags:
  - degree/mathsforcs/linearalgebra
---
![[Linear Algebra MOC 🌍]]

### Eigenvalues and Eigenvectors

The Eigenvectors of a matrix are non-zero vectors where
$$
A \mathbf{x} = \lambda \mathbf{x}
$$
They're only scaled in length, and that scalar $\lambda$ is the vector's Eigenvalue.

>[!attention] 
>Although the transformation does not change the direction of the vector, they can reverse them with negative eigenvalues.

##### Example:

Take the matrix
$$
A = \begin{bmatrix}3 & 0 \\ 8 & -1\end{bmatrix}
$$
Transforming the vector $\mathbf{x} = \begin{bmatrix}1 \\ 2\end{bmatrix}$ by $A$ gives
$$
A \mathbf{x} = \begin{bmatrix}
3 & 0 \\ 8 & -1
\end{bmatrix}
\begin{bmatrix}
1 \\ 2
\end{bmatrix}
=
\begin{bmatrix}
3 \\ 6
\end{bmatrix}
=3 \mathbf{x}
$$
Which makes $\mathbf{x}$ an eigenvector, with $3$ as it's eigenvalue.

---
### Derivation of the Characteristic Equation

An eigenvector is a vector such that
$$
A \mathbf{x} = \lambda \mathbf{x}
$$
But the left is matrix-vector multiplication and the right is vector-scalar multiplication. So let's turn the right into matrix-vector.
$$
A \mathbf{x} = \lambda I \mathbf{x}
$$
Now we can make it equal to zero and factor out $\mathbf{x}$.
$$
\begin{align*}
A \mathbf{x} - \lambda I \mathbf{x} &= \vec{\mathbf{0}}\\
\\
(A - \lambda I) \mathbf{x} &= \vec{\mathbf{0}}
\end{align*}
$$
And from this we can determine that
$$
\det(A - \lambda I) = 0
$$

>[!info] 
>$\det(A - \lambda I)=0$ is called the characteristic equation of $A$.

---
### Finding Eigenvalues and Eigenvectors

If $A$ is an $n \times n$ matrix, then $\lambda$ is an eigenvalue of $A$ iff it satisfies $\det(A - \lambda I) = 0$.

Take the matrix
$$
A=\begin{bmatrix}1 & -1 \\ 2 & 4\end{bmatrix}
$$

To find the eigenvalues $\lambda$, we have to solve $\det(A - I \lambda)=0$.
$$
\begin{align*}
\det \left(\begin{bmatrix}
1-\lambda & -1\\
2 & 4-\lambda
\end{bmatrix}\right) &= 0\\
\\
(1-\lambda)(4-\lambda)+2 &= 0\\
\\
(\lambda-2)(\lambda-3) &= 0
\end{align*}
$$
So our eigenvalues are $\lambda=2$ and $\lambda=3$.

> [!note] 
> $(\lambda - 2)(\lambda - 3)$ is called the characteristic polynomial of $A$. And the highest power of $\lambda$ is the order of $A$. Here that would be 2.

And so now substitute $\lambda$ into the equation
$$
\begin{bmatrix}
A-I\lambda
\end{bmatrix}
\begin{bmatrix}
a \\ b
\end{bmatrix}=\begin{bmatrix}
0 \\ 0
\end{bmatrix}
$$

For $\lambda=2$
$$
\begin{align*}
\begin{bmatrix}
-1 & -1\\
2 & 2
\end{bmatrix}\begin{bmatrix}
a\\
b
\end{bmatrix} &= \begin{bmatrix}
0\\
0
\end{bmatrix}\\
\\
-a-b&=0\\
a &= -b
\end{align*}
$$
Now you just pick a value for $a$ like $a=1$. Then find the corresponding $b$, so $b=-1$.

So an eigenvector for $\lambda=2$ is $\begin{bmatrix}1 \\ -1\end{bmatrix}$.

---
### Finding Eigenvalues, the Quick Way

For a $2 \times 2$ matrix $M$
$$
M=\begin{bmatrix}
a & b \\ c & d
\end{bmatrix}
$$
We can quickly find the eigenvalues, if we work out the mean of $a$ and $d$, and the determinant $ad-bc$.

Then using the formula
$$
\lambda = m \pm \sqrt{m^{2} - p}
$$
where $m$ is the mean of $a$ and $d$ and $p$ is the determinant.

##### Example
Take the matrix from the long way example.
$$
A=\begin{bmatrix}1 & -1 \\ 2 & 4\end{bmatrix}
$$
The mean of $a$ and $d$ is $\frac{5}{2}$ and the determinant is $(4)-(-2)=6$.
Now just put them in the formula and simplify
$$
\begin{align*}
\lambda &= \frac{5}{2} \pm \sqrt{\left(\frac{5}{2}\right)^{2} - 6}\\
\\
&= \frac{5}{2} \pm \sqrt{\frac{25}{4} - \frac{24}{4}}\\
\\
&= \frac{5}{2} \pm \sqrt{\frac{1}{4}}\\
\\
&= \frac{5}{2} \pm \frac{1}{2}\\
\\
\therefore \lambda &= 3\\
\lambda &= 2
\end{align*}
$$

---
### Eigenspace

The eigenspace of a matrix $A$ is the set of all eigenvectors corresponding to an eigenvalue $\lambda_{0}$.

The [[Linear Maps#Null Space or Kernel|Null Space]] of $A - \lambda_{0} I$ is equal to the eigenspace, as
$$
(A - \lambda_{0} I) \mathbf{x} = \vec{\mathbf{0}}
$$

##### Example

Find the basis of the eigenspace of $A$ corresponding to $\lambda=-8$.
$$
A = 
\begin{bmatrix}
2 & -1 \\ 10 & -9
\end{bmatrix}
$$
First, form the equation $(A + 8\lambda) \mathbf{x} = \mathbf{b}$. This gives us the expression
$$
\begin{bmatrix}
10 & -1 \\ 10 & -1
\end{bmatrix}
\begin{bmatrix}
x_{1} \\ x_{2}
\end{bmatrix}
=
\begin{bmatrix}
0 \\ 0
\end{bmatrix}
$$
Which forms the system
$$
\begin{cases}
10x_{1} - x_{2} &= 0 \\
10x_{1} - x_{2} &= 0
\end{cases}
$$

So $x_{2} = 10x_{1}$.
So all vectors in this eigenspace are in the form $(x, 10x)$. So one basis could be $\{(1,10)\}$.

Doing the same for the eigenspace of $A$ corresponding to $\lambda = 1$.
$$
\begin{bmatrix}
1 & -1 \\ 10 & -10
\end{bmatrix}
\begin{bmatrix}
x_{1} \\ x_{2}
\end{bmatrix}
=
\begin{bmatrix}
0 \\ 0
\end{bmatrix}
$$
Which forms the system
$$
\begin{cases}
x_{1} - x_{2} &= 0 \\
10x_{1} - 10x_{2} &= 0
\end{cases}
$$
So $x_{2} = x_{1}$
So all vectors in this eigenspace are in the form $(x,x)$. So one basis could be $\{(1,1)\}$.

---
### Algebraic Multiplicity

Let $\lambda_{0}$ be an eigenvalue of a matrix $A$.

The algebraic multiplicity of $\lambda_{0}$ is the power $k$ with which $(\lambda - \lambda_{0})$ appears as a factor of the characteristic polynomial.

For example, if
$$
\det(A - \lambda I)=(\lambda-2)^{3} (\lambda+5)^{2}
$$
Then the algebraic multiplicity of $\lambda=2$ is $3$,
and the algebraic multiplicity of $\lambda=-5$ is $2$.

If an $n \times n$ matrix has $n$ distinct eigenvalues, then the algebraic multiplicity of all eigenvalues is $1$.

---
### Geometric Multiplicity

The geometric multiplicity of an eigenvalue $\lambda_{0}$ is the dimension of the eigenspace corresponding to $\lambda_{0}$.

---
### $A^{k}$ case

Take the matrix $A$ with the eigenvector $\mathbf{x}$ and eigenvalue $\lambda$.

If you multiply an eigenvector $\mathbf{x}$ by it's matrix $k$ times, the result will be $\lambda^{k}\mathbf{x}$.
$$
A^{k} \mathbf{x}=\lambda^{k} \mathbf{x}
$$

---
### $A^{-1}$ case

If you have matrix $A$ with eigenvector $x$ and eigenvalue $\lambda$, the eigenvalue of matrix $A^{-1}$ is $\frac{1}{\lambda}$.

---
### Complex Eigenvalues

Just like the real case, $\lambda \in \mathbb{C}$ is an eigenvalue of $A$ if $A \mathbf{x} = \lambda \mathbf{x}$ for a non-zero $\mathbf{x} \in \mathbb{C}^{n}$.

>[!important] 
>If $\lambda$ is an eigenvalue with $\mathbf{x}$ as its eigenvector.
>Then $\overline{\lambda}$ is an eigenvalue with the [[Complex Conjugate]] $\overline{\mathbf{x}}$ as its eigenvector.

Take matrix $A$
$$
A = 
\begin{bmatrix}
-2 & -1 \\ 5 & 2
\end{bmatrix}
$$
Computing the characteristic equation of $A$, we get
$$
\lambda^{2} + 1 = 0
$$
Therefore $\lambda = i$ and $\lambda = -i$.

If $A$ is a real [[Matrices#Symmetric Matrices|Symmetric]] matrix then all the eigenvalues of $A$ are real.

Take the real matrix $C$.
$$
C = \begin{bmatrix}
a & -b \\ b & a
\end{bmatrix}
$$
The eigenvalues of $C$ are $\lambda = a \pm bi$.

If both $a,b$ are not zero, then $C$ can be factored as
$$
\begin{bmatrix}
a & -b \\ 
b & a
\end{bmatrix}=
\begin{bmatrix}
|\lambda| & 0 \\ 
0 & |\lambda|
\end{bmatrix}
\begin{bmatrix}
\cos \theta & - \sin \theta \\ 
\sin \theta & \cos \theta
\end{bmatrix}
$$
where $\theta = \arg \lambda$.

Geometrically, $C$ is equal to a rotation by $\theta$ then a scaling by $|\lambda|$.

##### Example

Find the eigenvalues of the matrix $A$
$$
A = \begin{bmatrix}
3 & 0 & 0 \\ 
2 & 1 & -1 \\ 
0 & 2 & 3
\end{bmatrix}
$$

The characteristic equation is $(\lambda - 3)(\lambda^{2} - 4 \lambda + 5)$.

This gives us
$$
\begin{align*}
\lambda_{1} &= 3\\
\lambda_{2} &= 2+i\\
\lambda_{3} &= 2-i
\end{align*}
$$

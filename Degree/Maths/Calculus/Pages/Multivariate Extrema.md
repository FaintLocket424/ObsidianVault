---
tags:
  - degree/mathsforcs/calculus
---
![[Calculus MOC 🌍]]

### Bivariate Extrema 

Differentiating $f_{x}$ and $f_{y}$ again gets us $f_{xx}$, $f_{xy}$, $f_{yx}$ and $f_{yy}$.

For most $C^{2}$ functions $f_{xy} = f_{yx}$, but not always.

We gather these derivatives in the Hessian Matrix.
$$
\mathbf{H}_{f} = \begin{bmatrix}
\frac{\partial^{2} f}{\partial x^{2}} & \frac{\partial^{2} f}{\partial x \partial y} \\ 
\frac{\partial^{2} f}{\partial y \partial x} & \frac{\partial^{2} f}{\partial y^{2}}
\end{bmatrix} = 
\begin{bmatrix}
f_{xx} & f_{xy} \\ 
f_{yx} & f_{yy}
\end{bmatrix}
$$
$\mathbf{H}_{f}$ is also the [[Vector Valued Functions#The Jacobian Matrix|Jacobian]] of $\nabla_{f}$.

The test for bivariate extrema is:
- $(x_{0},y_{0})$ is a local maximum if $\det \mathbf{H}_{f} > 0$ and $f_{xx} < 0$
- $(x_{0},y_{0})$ is a local minimum if $\det \mathbf{H}_{f} > 0$ and $f_{xx} > 0$
- $(x_{0},y_{0})$ is a saddle point if $\det \mathbf{H}_{f} < 0$.
- If $\det \mathbf{H}_{f}$ then the test is inconclusive.

---
### Approximations 

For a multivariate function, the linear approximation is
$$
f(\mathbf{x_{0}} + \mathbf{v}) \approx f(\mathbf{x_{0}}) + \nabla f (\mathbf{x_{0}}) \mathbf{v}
$$

The 2nd order gives us a better, quadratic approximation.
$$
f(\mathbf{x_{0}} + \mathbf{v}) \approx f(\mathbf{x_{0}}) + \nabla f (\mathbf{x_{0}})v + \frac{1}{2} \mathbf{v}^{T} \mathbf{H}_{f}(\mathbf{x_{0}}) \mathbf{v}
$$
And at a stationary point the 2nd term is zero so
$$
f(\mathbf{x_{0}} + \mathbf{v}) \approx f(\mathbf{x_{0}}) + \frac{1}{2} \mathbf{v}^{T} \mathbf{H}_{f}(\mathbf{x_{0}}) \mathbf{v}
$$

---
### 2nd Derivative Test and Eigenvalues 

At a stationary point $\mathbf{x}_{0}$ the quadratic approximation is
$$
f(\mathbf{x_{0}} + \mathbf{v}) \approx f(\mathbf{x_{0}}) + \frac{1}{2} \mathbf{v}^{T} \mathbf{H}_{f}(\mathbf{x_{0}}) \mathbf{v}
$$

But $\mathbf{H}_{f}(\mathbf{x}_{0})$ is real and symmetric, therefore it has orthogonal eigenvectors $e_{1},\ldots, e_{n}$ with eigenvalues $\lambda_{1}, \ldots, \lambda_{n} \in \mathbb{R}$.

We can then write $\mathbf{v}$ as a linear combination of these eigenvectors.
$$
\begin{align*}
f(\mathbf{x_{0}} + \mathbf{v}) &\approx  f(\mathbf{x_{0}}) + \frac{1}{2} (c_{1}e_{1} + \cdots, c_{n}e_{n})^{T} \mathbf{H}_{f}(\mathbf{x_{0}}) (c_{1}e_{1} + \cdots, c_{n}e_{n})\\
\\
&\approx f(\mathbf{x}_{0}) + \frac{\lambda_{1}}{2} c_{1}^{2} + \cdots + \frac{\lambda_{n}}{2} c_{n}^{2}
\end{align*}
$$
So, if all $\lambda_{i}$ are positive, it's a u-parabola.
If all $\lambda_{i}$ are negative, it's an n-parabola.
If there are $\lambda$s with different signs, it's a saddle.

This can be summarised in some rules:
- $(x_{0}, y_{0})$ is a local maximum if the eigenvalues of $\mathbf{H}_{f}(x_{0}, y_{0})$ are all positive.
- $(x_{0}, y_{0})$ is a local minimum if all the eigenvalues of $\mathbf{H}_{f}(x_{0}, y_{0})$ are negative.
- $(x_{0}, y_{0})$ is a saddle if some eigenvalues of $\mathbf{H}_{f}(x_{0}, y_{0})$ are positive and some are negative.
- If $\mathbf{H}_{f}(x_{0}, y_{0})$ is singular, has no eigenvalues, then the test is inconclusive.

##### Example 

Identify the nature of the stationary points of
$$
f(x,y,z) = x^{2} + y^{2} + z^{2} - xy - 2z
$$

Find the stationary points by solving 
$$
\begin{align*}
\begin{Bmatrix}
f_{x} &= 0 \\ 
f_{y} &= 0 \\ 
f_{z} &= 0
\end{Bmatrix}
&= 
\begin{Bmatrix}
2x-y &= 0 \\ 
2y-x &= 0 \\ 
2z-2 &= 0
\end{Bmatrix}\\
\\
&=
\begin{Bmatrix}
y &= 2x \\ 
3x &= 0 \\ 
z &= 1
\end{Bmatrix}\\
\\
&=
\begin{Bmatrix}
x &= 0 \\ 
y &= 0 \\ 
z &= 1
\end{Bmatrix}
\end{align*}
$$
So there is a single stationary point $\mathbf{x}_{0} = (0,0,1)$.

So the Hessian at $\mathbf{x}_{0}$ is
$$
\mathbf{H}_{f}(0,0,1) = \begin{bmatrix}
2 & -1 & 0 \\ 
-1 & 2 & 0 \\ 
0 & 0 & 2
\end{bmatrix}
$$
Then to find the eigenvalues of the above
$$
\begin{align*}
|\mathbf{H}_{f}(0,0,1) - \lambda I| &= 0\\
\\
\left|\begin{matrix}
2 - \lambda & -1 & 0\\
-1 & 2-\lambda & 0\\
0 & 0 & 2-\lambda
\end{matrix}\right| &= 0
\end{align*}
$$
This gives us the characteristic equation 
$$
(2-\lambda)^{3}-(2-\lambda)=0
$$
Which has roots $\lambda=2$, $\lambda = 1$ and $\lambda=3$.
Since all of these are positive, the stationary point is a minimum.

---
### Additional Information

- [[Maths for CS Calculus Topic 5 Multivariate Extrema.pdf|Maths for CS Calculus Topic 5 Multivariate Extrema]]
- [[Maths for CS Calculus Topic 11 Multivariate Extrema cont.pdf]]
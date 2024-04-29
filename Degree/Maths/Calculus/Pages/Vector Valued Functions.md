---
tags:
  - degree/mathsforcs/calculus
---
![[Calculus MOC 🌍]]

### Vector Valued Functions 

$$
\mathbf{f}: \mathbb{R}^{n} \to \mathbb{R}^{m}
$$
A vector valued function is one in which the output is a vector
$$
(f_{1}(\mathbf{x}), f_{2}(\mathbf{x}), \ldots, f_{n}(\mathbf{x}))
$$
So the derivative of the $i$th component of the output with respect to the $j$th input is
$$
\frac{\partial f_{i}}{\partial x_{j}}
$$

---
### The Jacobian Matrix 

If we have a function $\mathbf{f} : \mathbb{R}^{n} \to \mathbb{R}^{m}$ where $\mathbf{f}=(f_{1}(\mathbf{x}), f_{2}(\mathbf{x}), \ldots, f_{m}(\mathbf{x}))$.

We set
$$
\mathbf{J}_{ij} = \frac{\partial f_{i}}{\partial x_{j}}
$$
This creates a matrix of partial derivatives called the Jacobian matrix.
$$
\mathbf{J} = \begin{bmatrix}
\frac{\partial f_{1}}{\partial x_{1}} & \cdots & \frac{\partial f_{1}}{\partial x_{n}} \\ 
\vdots & \ddots & \vdots \\ 
\frac{\partial f_{m}}{\partial x_{1}} & \cdots & \frac{\partial f_{m}}{\partial x_{n}}
\end{bmatrix}
$$
So the $i$th row of the Jacobian matrix of $\mathbf{f}$ is the gradient $\nabla f_{i}$ transposed.

And the $j$th column is the derivative of $\mathbf{f}$ w.r.t. $x_{j}$ which is $\frac{\partial \mathbf{f}}{\partial x_{j}}$.

---
### Composite Functions with the Jacobian 

Say we have two functions 
$$
\begin{align*}
\mathbf{f} : \mathbb{R}^{3} \to \mathbb{R}^{2} &= (2x_{1} + x_{2} - x_{3}, x_{1} + 3x_{2} - 4x_{3})\\
\mathbf{g} : \mathbb{R}^{2} \to \mathbb{R}^{2} &= (\sin(x_{1} + x_{2}), \cos(x_{1} - x_{2}))
\end{align*}
$$
So the Jacobians of these functions are 
$$
\begin{align*}
\mathbf{J}_{f} &= \begin{bmatrix}
2 & 1 & -1 \\ 
1 & 3 & -4
\end{bmatrix}\\
\\
\mathbf{J}_{g} &= \begin{bmatrix}
\cos(x_{1} + x_{2}) & \cos(x_{1} + x_{2})\\
- \sin(x_{1} - x_{2}) & \sin(x_{1} - x_{2})
\end{bmatrix}
\end{align*}
$$
To get the Jacobian of $g \circ f$
$$
\mathbf{J}_{g \circ f} = \mathbf{J}_{g} \mathbf{J}_{f}
$$

---
### Linear Approximations 

For the multivariate function $\mathbf{f} : \mathbb{R}^{n} \to \mathbb{R}^{m}$, the Jacobian matrix gives the best linear approximation of $\mathbf{f}$ at $\mathbf{x}$
$$
f(\mathbf{x} + h \mathbf{v}) \approx \mathbf{f}(\mathbf{x}) + \mathbf{J}_{\mathbf{f}}(\mathbf{x})(h \mathbf{v})
$$
>[!note] 
>$x$, $v$ and $hv$ are all $n$-dimensional vectors.
>$\mathbf{J}_{f}(x)$ is an $m \times n$ matrix.
>$f(x)$ and $\mathbf{J}_{\mathbf{f}}(x)(h \mathbf{v})$

##### Example: 

Find an approximation to $\mathbf{g} : \mathbb{R}^{2} \to \mathbb{R}^{2}$ near $\left(\frac{3\pi}{4}, \frac{\pi}{4}\right)$.
$$
\mathbf{g}(x_{1},x_{2}) = (\sin(x_{1} + x_{2}), \cos(x_{1} - x_{2}))
$$
First we work out the Jacobian of $\mathbf{g}$
$$
\mathbf{J}_{g} = \begin{bmatrix}
\cos(x_{1} + x_{2}) & \cos(x_{1} + x_{2}) \\ 
-\sin(x_{1} - x_{2}) & \sin(x_{1} - x_{2})
\end{bmatrix}
$$
Next we work out the value of the Jacobian at the point $\left(\frac{3\pi}{4}, \frac{\pi}{4}\right)$
$$
\begin{align*}
\mathbf{J}_{g}\left(\frac{3\pi}{4}, \frac{\pi}{4}\right) &= \begin{bmatrix}
\frac{\partial g_{1}}{\partial x_{1}} & \frac{\partial g_{1}}{\partial x_{2}} \\ 
\frac{\partial g_{2}}{\partial x_{1}} & \frac{\partial g_{2}}{\partial x_{2}}
\end{bmatrix} \\
\\
&= 
\begin{bmatrix}
\cos(\pi) & \cos(\pi) \\ 
-\sin\left(\frac{\pi}{2}\right)& \sin\left(\frac{\pi}{2}\right)
\end{bmatrix} \\
\\
&= 
\begin{bmatrix}
-1 & -1 \\ 
-1 & 1
\end{bmatrix}
\end{align*}
$$
So near $\left(\frac{3\pi}{4}, \frac{\pi}{4}\right)$ we can approximate $\mathbf{g}$ by
$$
\mathbf{g}\left(\frac{3\pi}{4} + \delta_{x}, \frac{\pi}{4} + \delta_{y} \right) = \mathbf{g}\left(\frac{3\pi}{4}, \frac{\pi}{4}\right) + \begin{bmatrix}
-1 & -1 \\ -1 & 1
\end{bmatrix}
\begin{bmatrix}
\delta_{x} \\ \delta_{y}
\end{bmatrix}
$$






---
### Additional Information

- [[Maths for CS Calculus Topic 7 Vector Valued Functions.pdf]]

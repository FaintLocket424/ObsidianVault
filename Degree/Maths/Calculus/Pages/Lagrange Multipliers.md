---
tags:
  - degree/mathsforcs/calculus
---
![[Calculus MOC 🌍]]

### Constrained Optimisation

Just like with regular [[Multivariate Extrema]], the goal is to min-max a function $f(x_1,x_2,\dots,x_n)$ but where $x_1,\dots,x_n$ are not independent.

You can think of it as finding the minimum point of the intersection between two functions.

We can't just use the regular method of finding critical points because those points probably won't satisfy the condition we're looking for.

If we have the function $f(x,y)$ and $g(x,y)$, we can solve:
$$
\begin{cases}
f_{x}&=\lambda g_{x} \\
f_{y}&=\lambda g_{y} \\
g&=0
\end{cases}
$$
Where $\lambda$ here is the *Lagrange Multiplier*.
###### Example:
$$
\begin{align*}
f(x,y)&=x^{2}+y^{2}\\
g(x,y)&=xy-3
\end{align*}
$$
Using the system of equations we have above:
$$
\begin{align*}
\begin{Bmatrix}
f_{x}&=\lambda g_{x} \\
f_{y}&=\lambda g_{y} \\
g&=0
\end{Bmatrix}&=
\begin{Bmatrix}
2x&=\lambda y \\
2y&=\lambda x \\
xy&=3
\end{Bmatrix}\\\\
&=
\begin{Bmatrix}
2x&=\frac{3\lambda}{x} \\
2 \frac{3}{x}&=\lambda x \\
y&=\frac{3}{x}
\end{Bmatrix}\\\\
&=
\begin{Bmatrix}
x^{2}=\frac{3}{2}\lambda  \\
x^{2}=\frac{6}{\lambda} \\
y=\frac{3}{x}
\end{Bmatrix}
\end{align*}
$$
So $\frac{3}{2}\lambda =\frac{6}{\lambda}$, $\therefore \lambda = \pm 2$

For $\lambda=2$, we get two solutions of $(\sqrt{3},\sqrt{3})$ and $(-\sqrt{3},-\sqrt{3})$
For $\lambda=-2$, we get no solutions.

---
### The Method:

For a function $f(\boldsymbol{x})$ subject to the constraint $g(\boldsymbol{x})=0$:

1. We define the Lagrangian:
$$
\begin{align*}
	L(\boldsymbol{x},\lambda)=f(\boldsymbol{x})-\lambda g(\boldsymbol{x})
\end{align*}
$$
2. We find the stationary points of $L$ with respect to both $\boldsymbol{x}$ and $\lambda$. Aka, we solve the system $\nabla f(\boldsymbol{x})=\lambda \nabla g(\boldsymbol{x})$ and $g(\boldsymbol{x})=0$ for $\boldsymbol{x}$ and $\lambda$.

3. Then the constrained extrema are found among the solutions to these equations.


---
### Example:

Find the local minimum and maximum values of $f(x,y) = x^{2}+x+2y^{2}$ subject to the constraint $g(x,y) = x^{2}+y^{2}-1$.

$$
\begin{cases}
f_{x} &= \lambda g_{x} \\
f_{y} &= \lambda g_{y} \\
g &= 0
\end{cases}=
\begin{cases}
2x+1 &= \lambda 2x \\
4y &= \lambda 2y \\
x^{2}+y^{2}-1 &= 0
\end{cases}
$$

$$
\begin{align*}
4y &= \lambda 2y\\\\
\therefore \lambda &= 2\\
x &= \frac{1}{2}\\
y &= \pm \frac{\sqrt{3}}{2}
\end{align*}
$$

So we have the points $(\frac{1}{2},\frac{\sqrt{3}}{2},\frac{9}{4})$ and $(\frac{1}{2},-\frac{\sqrt{3}}{2},\frac{9}{4})$.

And from dividing by $y$, we need to account for $y=0$.
$$
\begin{align*}
y &= 0\\
x &= \pm 1
\end{align*}
$$
So we also get the points $(1,0,2)$ and $(-1,0,0)$.

From looking at the $z$ coordinates, we can see that $\left(\frac{1}{2},\frac{\sqrt{3}}{2},\frac{9}{4}\right)$ and $\left(\frac{1}{2},-\frac{\sqrt{3}}{2},\frac{9}{4}\right)$ are local maximums and $(-1,0,0)$ is a local minimum.

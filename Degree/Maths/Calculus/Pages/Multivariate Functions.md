---
tags:
  - degree/mathsforcs/calculus
---
![[Calculus MOC 🌍]]

### Functions of Multiple Variables 

A function $f: \mathbb{R} \times \mathbb{R} \to \mathbb{R}$ can be viewed as a 2D surface. e.g.
$$
f(x,y) = 2x^{2}y^{3} - xy + 2x - 3y + 5
$$
---
### Fixing Values

Let's try fixing $x$ or $y$ to a value:
- If we fix $y=0$, then $f(x,0) = 2x+5$ which is a line.
- If we fix $y=1$, then $f(x,1) = 2x^{2} + x + 2$ which is a parabola.
- If we fix $x=0$, then $f(0,y)=-3y+5$ which is a line.

For a fixed $y$, we can work out the gradient in the $x$-direction at any point.

If we fix $y=0$
$$
\begin{align*}
f(x,0)&= 2x+5\\
\\
\frac{d(2x+5)}{dx} &= 2
\end{align*}
$$
So, at any point with $y=0$, the $x$-direction has a gradient of $2$.

---
### Differentiating Multivariate Functions 

Take the example equation
$$
f(x,y) = 2x^{2}y^{3} - xy + 2x - 3y + 5
$$
If we think of $y=y_{0}$ as a fixed unknown, then $f$ is just a function of $x$ and we can differentiate at $x=x_{0}$. We call this the *partial derivative of $f$ with respect to $x$*.
$$
\frac{\partial f}{\partial x}(x_{0}, y_{0}) = \lim_{x \to x_{0}} \frac{f(x, y_{0}) - f(x_{0}, y_{0})}{x-x_{0}}
$$
As with single-variable derivatives, $\frac{\partial f}{\partial x}$ is itself a function $\frac{\partial f}{\partial x}:A \to \mathbb{R}$, where $A \subseteq \mathbb{R}^{2}$ is the domain on which the limit exists.

So the partial derivative of our example function $f$ with respect with $x$
$$
\frac{\partial f}{\partial x} = \frac{\partial(2x^{2}y^{3} - xy + 2x - 3y + 5)}{\partial x} = 4xy^{3} - y + 2
$$
So, at the point $(1,3)$ the gradient in the $x$-direction is $4(1)(3)^{3} - 3 + 2=107$.

>[!tip] 
>Go get $4xy^{3} - y + 2$, we differentiate like normal but you treat $y$ the same as you treat normal numbers. So $-3y$ differentiates to $0$, with respect to $x$.

Then, if we do the same with $x$, fixing it to an unknown value we get the *partial derivative of $f$ with respect to $y$*.
$$
\frac{\partial f}{\partial y} = \frac{\partial (2x^{2}y^{3} - xy + 2x - 3y + 5)}{\partial y} = 6x^{2}y^{2} - x - 3
$$
So, at the point $(1,3)$ the gradient in the $y$-direction is $6(1)^{2}(3)^{2} - (1) - 3 = 50$.

We also have shorthand for partial derivatives.
$$
\small{\begin{align*}
\frac{\partial f}{\partial x} &= f_{x}\\
\\
\frac{\partial f}{\partial y} &= f_{y}
\end{align*}}
$$

---
### Directional Derivatives 

Consider a point $\mathbf{p} = (x_{0}, y_{0})$ and a direction given by a unit vector $\mathbf{v}=\small{\begin{bmatrix}v_{x} \\ v_{y}\end{bmatrix}}$.

The directional derivative of $f(x,y)$ in the direction $\mathbf{v}$ is defined to be
$$
\begin{align*}
\nabla_{\mathbf{v}} f(x_{0},y_{0}) &= \lim_{h \to 0} \frac{f(x_{0} + h \cdot v_{x}, y_{0} + h \cdot v_{y}) - f(x_{0},y_{0})}{h}\\
\\
&= \lim_{h \to 0} \frac{f(\mathbf{p} + h \cdot \mathbf{v}) - f(\mathbf{p})}{h}
\end{align*}
$$
This function gives the gradient of $f$ in the direction $\mathbf{v}$ at the point $\mathbf{p}$.

>[!info] 
>The symbol $\nabla$ is called nabla.
>It is pronounced 'del' when it is an operator, or grad when it is the result. Much the same as "derivative" and "gradient of" are used for single variate functions.

>[!tldr] Analogy
> - Think of the 2D function $f$ as a hill.
> - Take $x$ as north and $y$ as east.
> - $f_{x}$ would be how steep the hill is moving north.
> - $f_{y}$ would be how steep the hill is moving east.
> - $\nabla_{\mathbf{v}}f$ is the steepness of the hill in the direction $\mathbf{v}$. If we were moving north-east, it would be $\left(\frac{1}{\sqrt{2}},\frac{1}{\sqrt{2}}\right)$.

We say that $f$ is differentiable if for all unit vectors $\mathbf{v}$ we have a $\nabla_{v}f$.

>[!info] 
>This can be visualised that close to the point $(x,y)$, the function $f$ looks like a plane.

##### Example 

Take the function $f$
$$
f = 2x^{2}y^{3} - xy + 2x - 3y + 5
$$
And find the gradient at $(1,3)$ in the direction $\small{\left(\frac{1}{\sqrt{5}},\frac{2}{\sqrt{5}}\right)}$.
$$
\small{
\begin{align*}
&= \lim_{h \to 0} \frac{f\left(1 + \frac{h}{\sqrt{5}}, 3 + \frac{2h}{\sqrt{5}}\right)- f(1,3)}{h}\\
\\
&= \lim_{h \to 0} \frac{2\left(1 + \frac{h}{\sqrt{5}}\right)^{2} \left(3 + \frac{2h}{\sqrt{5}}\right)^{3} - \left(1 + \frac{h}{\sqrt{5}}\right)\left(3 + \frac{2h}{\sqrt{5}}\right) + 2\left(1 + \frac{h}{\sqrt{5}}\right) + 5 - 49}{h}\\
\\
&= \lim_{h \to 0} \frac{54-3+2-9+5-49+h(\frac{207}{\sqrt{5}}) + h^{2}(\cdots)}{h}\\
\\
&= \lim_{h \to 0} \frac{h \left(\frac{207}{\sqrt{5}}\right) + h^{2}(\cdots) + \cdots}{h}\\
\\
&= \lim_{h \to 0} \frac{207}{\sqrt{5}} + h(\cdots) = \frac{207}{\sqrt{5}}
\end{align*}
}
$$

Now that is the very long winded way to get the answer. There is a quicker way.

The slope in the direction $\mathbf{v}$ will be $v_{x}f_{x} + v_{y}f_{y}$.
$$
\nabla_{v}f = \mathbf{v}\begin{bmatrix}f_{x} \\ f_{y}\end{bmatrix}
$$
Which would make answering the previous question as simple as
$$
\begin{align*}
\nabla_\mathbf{v}f(1,3) &= \frac{1}{\sqrt{5}} \cdot 107 + \frac{2}{\sqrt{5}} \cdot 50 \\
\\
&= \frac{207}{\sqrt{5}}
\end{align*}
$$

---
### Linear Approximations 

For a univariate function the derivative gives the tangent line.
$$
f'(x) = \lim_{h \to 0} \frac{f(x+h) - f(x)}{h}
$$
For a given linear function, an approximation for $f$ near $x$ is
$$
f(x+h) \approx f(x) + hf'(x)
$$

>[!note] 
>This is actually a 1st order [[Taylor Series#First Taylor Polynomial|Taylor Polynomial]].


We know that $\nabla_{\mathbf{v}}f(\mathbf{p})$ is the slope in the direction $\mathbf{v}$.
So a linear approximation would be
$$
f(\mathbf{p} + h \mathbf{v}) \approx f(\mathbf{p}) + h \mathbf{v} \nabla f(\mathbf{p})
$$

---
### Functions of Multiple Real Variables 

Just as we can have univariate functions $f(x)$ and bivariate functions $f(x,y)$, we can have functions of as many variables as we'd like.

A function with $n$ input variables $\mathbb{R}^{n} \to \mathbb{R}$ would be
$$
f(x_{1},x_{2},\ldots,x_{n})
$$
This function produces an $n$ dimensional surface in $n+1$ dimensional space.
E.g. an $\mathbb{R}^{2} \to \mathbb{R}$ function produces a 2 dimensional surface in a 3 dimensional space.

In general, the calculus doesn't change with more variables.
$$
\frac{\partial f}{\partial x_{i}} (\mathbf{x}) = \lim_{h \to 0} \frac{f(\mathbf{x} + h \cdot \mathbf{e_{i}}) - f(\mathbf{x})}{h}
$$
And so
$$
\nabla f = \left(\frac{\partial f}{\partial x_{1}}, \frac{\partial f}{\partial x_{2}}, \ldots, \frac{\partial f}{\partial x_{n}} \right)^{T}
$$
So $f$ is differentiable at $x_{0}$ if for all unit vectors $\mathbf{v}$ we have:
$$
\nabla_{\mathbf{v}} f (\mathbf{x_{0}}) = \mathbf{v} \cdot \nabla f
$$

---
### Multivariate Chain Rule 

For $f \circ g(x)$, the chain rule says
$$
\frac{df}{dx} = \frac{df}{dg} \frac{dg}{dx}
$$
For $f(x,y): \mathbb{R}^{2} \to \mathbb{R}$, where $x$ and $y$ are functions of $s$ and $t$, what is $\frac{\partial f}{\partial t}$?
$$
\frac{\partial f}{\partial t} = \frac{\partial f}{\partial x} \frac{\partial x}{\partial t} + \frac{\partial f}{\partial y} \frac{\partial y}{\partial t}
$$
So, this is the amount $f$ is varied by $t$ through $x$, plus the amount $f$ is varied by $t$ through $y$.






---
### Additional Information

- [Wikipedia]
- [Lecture Notes]
- [Maybe Practical Q and As]

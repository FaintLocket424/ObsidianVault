---
tags:
  - degree/mathsforcs/calculus
---
![[Calculus MOC 🌍]]

[[Forward Mode Automatic Differentiation|Forward Mode]] requires $n$ passes to compute the full gradient $\nabla f$.

But reverse mode can compute $\nabla f$ in one pass.

Suppose we have the function $e(f(g(h(x))))$.
The chain rule says 
$$
\frac{de}{dx} = \frac{de}{df} \frac{df}{dg} \frac{dg}{dh} \frac{dh}{dx}
$$
Instead of working from the inside, we work from the outside.
$$
\begin{align*}
\frac{de}{de} &= 1\\
\frac{de}{df} &= \frac{de}{de} \frac{de}{df}\\
\frac{de}{dg} &= \frac{de}{df} \frac{df}{dg}\\
\frac{de}{dh} &= \frac{de}{dg} \frac{dg}{dh}\\
\frac{de}{dx} &= \frac{de}{dh} \frac{dh}{dx}
\end{align*}
$$

$$
\bar{v}_{i} = \frac{\partial y}{\partial v_{i}}
$$

---
### Example 

Take the equation 
$$
y(x_{1},x_{2}) = \ln(x_{1}) + x_{1}x_{2} - \sin(x_{2})
$$
at the point $(2,5)$.

Here is the forward trace.
$$
\begin{align*}
v_{-1} &= x_{1} &= 2\\
v_{0} &= x_{2} &= 5\\
v_{1} &= \ln v_{-1} &= \ln 2\\
v_{2} &= v_{-1} \times v_{0} &= 2 \times 5\\
v_{3} &= \sin v_{0} &= \sin 5\\
v_{4} &= v_{1} + v_{2} &= 0.693 + 10\\
v_{5} &= v_{4} - v_{3} &= 10.693 + 0.959\\
y &= v_{5} &= 11.652
\end{align*}
$$
---
**Notation:** $\newcommand{\part}[2]{\frac{\partial #1}{\partial #2}}\bar {v}_i=\part{y}{v_i}$

We start with $y=v_5$ where
$$\bar v_5=\part{y}{v_5}=1$$

---
Then we move up the table to $v_5=v_4-v_3$.
We can see that $v_4$ is going to have an impact on $v_5$. And we can see that $\part{v_5}{v_4}=1$ if we differentiate $v_5$ with respect to $v_4$.
$$\bar v_4=\bar v_5\part{v_5}{v_4}=\bar v_5\times1=1$$
We then do the same for $v_3$.
$$\bar v_3=\bar v_5\part{v_5}{v_3}=\bar v_5\times-1=-1$$

---
Next we move another equation up in the table to $v_4=v_1+v_2$.
We can see $v_1$ is going to impact $v_4$, giving us:
$$\bar v_1=\bar v_4\part{v_4}{v_1}=1\times1=1$$
We use our value of $\bar v_4$ from above.

Then we do the same for $v_2$:
$$\bar v_2=\bar v_4\part{v_4}{v_2}=1\times1=1$$

---
Next we move another equation up to $v_3=\sin v_0$. We can see $v_0$ will have an impact on this one:
$$\bar v_0=\bar v_3\part{v_3}{v_0}=(-1)\times\cos v_0=-0.284$$

---
Next we move up again to the next equation $v_2=v_{-1}\times v_0$ where $v_{-1}$ and $v_0$ have an impact here.
$$\bar v_{-1}=\bar v_2\part{v_2}{v_{-1}}=1\times5=5$$

But with $\bar v_0$ is gets more complex since we've already worked out a value for $\bar v_0$, $-0.284$. So we just add the new section onto it.
$$\bar v_0=-0.284+\bar v_2\part{v_2}{v_0}=-0.284+1\times2=1.716$$

---
Next equation! $v_1=\ln(v_{-1})$. Here $v_{-1}$ impacts the result.
$$\bar v_{-1}=5+\bar v_1\part{v_1}{v_{-1}}=5+1\times\frac{1}{v_{-1}}=5.5$$

---
Next equation! $v_0=x_2$
$$\bar x_2=\bar v_0\part{v_0}{x_2}=1.716\times1=1.716$$

---
Next equation! $v_{-1}=x_1$
$$\bar x_1=\bar v_{-1}\part{v_{-1}}{x_1}=5.5\times1=5.5$$

---
Therefore $\nabla y(2,5)=\small{\begin{bmatrix}5.5  \\ 1.716\end{bmatrix}}$

---
### Additional Information

- [Wikipedia]
- [[Maths for CS Calculus Topic 6 Automatic Differentiation.pdf]]
- [Maybe Practical Q and As]

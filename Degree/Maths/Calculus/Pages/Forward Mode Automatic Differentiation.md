---
tags:
  - degree/mathsforcs/calculus
---
![[Calculus MOC 🌍]]

### Forward Mode Automatic Differentiation 

Suppose we have a function $e(f(g(h(x))))$.

The chain rule says
$$
\begin{align*}
\frac{de}{dx} &= \frac{de}{df} \frac{df}{dx}\\
&= \frac{de}{df} \frac{df}{dg} \frac{dg}{dx}\\
&= \frac{de}{df} \frac{df}{dg} \frac{dg}{dh} \frac{dh}{dx}
\end{align*}
$$
If we work from the inside, we only need to do one step at a time.
$$
\begin{align*}
\frac{dh}{dx} &= \frac{dh}{dx}\\
\frac{dg}{dx} &= \frac{dg}{dh} \frac{dh}{dx}\\
\frac{df}{dx} &= \frac{df}{dg} \frac{dg}{dx}\\
\frac{de}{dx} &= \frac{de}{df} \frac{df}{dx}
\end{align*}
$$
As long as each function is simple, this is no trouble.

Recall that
![[Multivariate Functions#Multivariate Chain Rule]]

---
### Example 

$$
y(x_{1},x_{2}) = \ln(x_{1}) + x_{1}x_{2} - \sin (x_{2})
$$
At the point $(2,5)$.

##### Step 1: Create a computational graph from atomic operations 
![[Pasted image 20240212121838.png]]

The forward primal trace is then:
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

##### Step 2 Compute Partial Derivatives 

$$
\begin{align*}
\dot{v}_{-1} &= \dot{x}_{1}\\
\dot{v}_{0} &= \dot{x}_{2}\\
\dot{v}_{1} &= \frac{v_{-1}}{v_{-1}}\\
\dot{v}_{2} &= \dot{v}_{-1}v_{0} + \dot{v}_{0}v_{-1}\\
\dot{v}_{3} &= \dot{v}_{0} \cos v_{0}\\
\dot{v}_{4} &= \dot{v}_{1} + \dot{v}_{2}\\
\dot{v}_{5} &= \dot{v}_{4} - \dot{v}_{3}\\
\dot{y} &= \dot{v}_{5}
\end{align*}
$$

##### Step 3: Trace in Direction
And doing a trace in the $x_{1}$ direction gives us:
$$
\begin{align*}
\dot{v}_{-1} &= 1\\
\dot{v}_{0} &= 0\\
\dot{v}_{1} &= \frac{1}{2}\\
\dot{v}_{2} &= 5\\
\dot{v}_{3} &= \cos 5\\
\dot{v}_{4} &= 5.5\\
\dot{v}_{5} &= 5.5\\
\dot{y} &= 5.5
\end{align*}
$$
So $\frac{\partial y}{\partial x_{1}}(2,5) = 5.5$

And so to find the gradient in the direction of the unit vector $(\frac{2}{\sqrt{5}}, \frac{1}{\sqrt{5}})$
$$
\begin{align*}
\dot{x}_{1} &= \frac{2}{\sqrt{5}}\\
\dot{x}_{2} &= \frac{1}{\sqrt{5}}\\
\dot{v}_{1} &= \frac{2}{\sqrt{5}}\\
\dot{v}_{2} &= \frac{12}{\sqrt{5}}\\
\dot{v}_{3} &= \frac{\cos 5}{\sqrt{5}}\\
\dot{v}_{4} &= \frac{13}{\sqrt{5}}\\
\dot{v}_{5} &= \frac{13 - \cos 5}{\sqrt{5}} \approx 5.69
\end{align*}
$$

---
### Additional Information

- [[Maths for CS Calculus Topic 6 Automatic Differentiation.pdf]]

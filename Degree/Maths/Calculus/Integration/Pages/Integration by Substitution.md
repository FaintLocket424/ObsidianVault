---
tags:
  - incomplete
  - degree/singlemathsa/integration
  - degree/mathsforcs/calculus/integration
---
![[Integration MOC 🌍]]

### Derivation 
Recall the [[Differentiation#Chain Rule|Chain Rule]]. If $u$ is a function of $x$, $u(x)$ and $g$ is a function of $u$, $g(u)$, then 
$$
\frac{dg}{dx} = \frac{dg}{du} \frac{du}{dx}
$$
If we spot an integrand of the form $f(u(x)) u'(x)$ and take $F(u)$ to be the antiderivative of $f(u)$ with respect to $u$ then
$$
\frac{dF}{dx} = \frac{dF}{du} \frac{du}{dx} = f(u) u'(x)
$$
Which is our original integrand.

Hence, $F(u(x))$ is the antiderivative of $f(u(x)) u'(x)$ with respect to $x$.

Therefore, we get the equation for integration by substitution.
##### The Equation 
$$
\int f(u(x)) u'(x) dx = F(u(x)) + c = F(u) + c = \int f(u) du
$$

---
### Example 1
Find 
$$
\int \frac{4x}{\sqrt{2x^{2} + 1}} dx
$$
We can recognise that 
$$
\frac{4x}{\sqrt{2x^{2}+1}} = \frac{1}{\sqrt{2x^{2} + 1}}4x = f(u) \frac{du}{dx}
$$
where $u = 2x^{2} + 1$ and $f(u)=\frac{1}{\sqrt{u}}$.

So 
$$
\begin{align*}
\int \frac{4x}{\sqrt{2x^{2}+1}} dx &= \int \frac{1}{\sqrt{u}}du\\
\\
&= 2\sqrt{u} + c\\
\\
&= 2 \sqrt{2x^{2} + 1} + c
\end{align*}
$$


---
### Additional Information

- [Wikipedia]
- [[Maths for CS Calculus Topic 13 Integration Part 1.pdf]]
- [[Maths for CS Calculus Topic 13 Integration Part 2.pdf]]
- [Maybe Practical Q and As]

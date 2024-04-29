---
tags:
  - degree/singlemathsa/integration
  - degree/mathsforcs/calculus/integration
aliases:
  - By Parts
---
![[Integration MOC 🌍]]

### Derivation 
Recall the [[Differentiation#Product Rule|Product Rule]]. If $u$ and $v$ are functions of $x$ then 
$$
\frac{d(uv)}{dx} = u'v + uv'
$$
Thus $uv$ is the antiderivative of $u'v + uv'$
$$
\int u'v dx + \int uv' dx = uv + c
$$
Rearranging this we get the equation 
$$
\int uv' dx = uv - \int u'v dx
$$
When selecting a $u$ and $v'$, you want the easily differentiable part to be $u$ and the easily integrable part to be $v'$. You want the resulting integral $\int u' v dx$ to be simpler than the original.

Also note that with definite integrals, you must keep the bounds consistent.
$$
\int^{b}_{a} u v' dx = \left[ uv \right]^{b}_{a} - \int^{b}_{a} u' v dx
$$

---
### Example 1
$$
\int x^{k} \ln(x) dx
$$
for some $k \in \mathbb{N}$

We see a product of terms and wonder if we can select $u$, $v$ in a way that will make things simpler.

Here if we select $u = x^{k}$ and $v' = \ln x$ then it is hard to proceed because we need $\int \ln(x)$, which is hard to find.

Instead, if we select $u = \ln(x)$ and $v' = x^{k}$, then $u' = \frac{1}{x}$ and $v = \frac{x^{k+1}}{k+1}$

So
$$
\int x^{k} \ln(x) dx = \frac{x^{k+1}}{k+1} \ln(x) - \int \frac{1}{x} \frac{x^{k+1}}{k+1} dx
$$
Which we can simplify to
$$
\frac{x^{k+1}}{k+1} \ln(x) - \frac{x^{k+1}}{(k+1)^{2}} + c
$$

---
### Additional Information

- [Wikipedia]
- [[Maths for CS Calculus Topic 13 Integration Part 1.pdf]]
- [[Maths for CS Calculus Topic 13 Integration Part 2.pdf]]
- [Maybe Practical Q and As]

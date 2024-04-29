---
tags:
  - incomplete
  - degree/singlemathsa/series
  - degree/mathsforcs/series
---
![[Series MOC 🌍]]

### Power Series 

A power series has the variable $x$ and a constant $x_{0}$ in the form 
$$
\sum_{n=0}^{\infty} a_{n}(x-x_{0})^{n} = a_{0} + a_{1}(x-x_{0}) + a_{2}(x-x_{0})^{2} + \cdots
$$
At any specific value of $x$ this becomes a normal series and we can use [[Convergence|Convergence Tests]] to determine convergence.

One power series is $\exp(x)$ 
$$
e^{x} = \sum_{n=0}^{\infty} \frac{x^{n}}{n!} = 1 + x + \frac{x^{2}}{2} + \frac{x^{3}}{3!} + \cdots + \frac{x^{n}}{n!} + \cdots
$$

---
### Radius of Convergence 

For an arbitrary power series $\sum^{\infty}_{n=0} a_{n} (x-x_{0})^{n}$, we can use the [[Convergence#Ratio Test|Ratio Test]].

$$
\lim_{n \to \infty} \left| \frac{a_{n+1} (x-x_{0})^{n+1}}{a_{n} (x-x_{0})^{n}} \right| = L
$$
If $L <1$ we have convergence. If $L>1$, divergence.

But for a specific value of $x$, $|x-x_{0}|$ is just a number, so:

If $\lim_{n \to \infty} \left| \frac{a_{n+1}}{a_{n}} \right| < \frac{1}{|x-x_{0}|}$ we have convergence. Otherwise, it's divergence.

Equivalently, we call $lim_{n \to \infty} \left| \frac{a_{n}}{a_{n+1}} \right| = r$ the radius of convergence.
- If $| x-x_{0}| <r$ we have absolute convergence.
- If $|x-x_{0}| >r$ we have divergence.
So $x$ must be between $x_{0}-r$ and $x_{0}+r$ for the series to converge.
If $x$ equals $x_{0}-r$ or $x_{0}+r$, the ratio test fails.

---
### Differentiation and Integration of Power Series

Take the power series $f$ with radius of convergence $r > 0$.
$$
f(x) = \sum^{\infty}_{n=0} a_{n} x^{n}
$$
Then, within the interval $(-r,r)$
- $f(x)$ is continuous
- $f'(x) = \sum^{\infty}_{n=1} n a_{n} x^{n-1}$
- $\int^{x}_{0} f(t) dt = \sum^{\infty}_{n=0} \frac{a_{n}}{n+1} x^{n+1}$

Both series $f'(x)$ and $\int^{x}_{0} f(t) dt$ have the same radius of convergence as $f(x)$.

---
### Power Series from Functions 

Suppose we have a function $f(x)$ and we wish to have a power series $\sum^{\infty}_{n=0} a_{n} x^{n}$ such that $f(x) = \sum^{\infty}_{n=0} a_{n} x^{n}$.

Observe that setting $x=0$ means $a_{0} = f(0)$.

Now we differentiate $f(x)$
$$
f'(x) = \sum^{\infty}_{n=1} n a_{n} x^{n-1}
$$
So $f'(0)=a_{1}$.

Then differentiating again 
$$
f''(x) = \sum^{\infty}_{n=2} n(n-1) a_{n} x^{n-2}
$$
So $f''(0)=2a_{2}$

Proceeding further, we see that 
$$
f^{(m)}(x) = \sum^{\infty}_{n=m} n(n-1) \ldots (n-m+1) a_{n} x^{n-m}
$$
Therefore, $f^{(m)}(0) = m! \cdot a_{m}$

##### MacLaurin Series 

$$
f(x) = f(0) + f'(0)x + f''(0) \frac{x^{2}}{2!} + f^{(3)}(0) \frac{x^{3}}{3!} + \cdots = \sum^{\infty}_{n=0}f^{(n)}(0) \frac{x^{n}}{n!}
$$
To use a MacLaurin series for some function $f$ we must have that
- $f \in C^{\infty}$
- The power series converges.

By recentering our series on $x_{0}$, we get a [[Taylor's MOC 🌍|Taylor Series]].


---
### Additional Information

- [[Maths for CS Calculus Topic 11 Power Series.pdf]]


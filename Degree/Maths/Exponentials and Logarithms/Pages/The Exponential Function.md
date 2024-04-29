---
tags:
  - degree/singlemathsa/exponentialfunction
---
![[Exponentials and Logarithms MOC 🌍]]

### The $\exp{x}$ function

For any real number $x$ we define the function $\exp{x}$ as:
$$
e^x=\exp{x}=\sum_{n=0}^{\infty}{\frac{x^n}{n!}}
$$

Note $\exp{0}=1$.

---
### Properties of the $\exp{x}$ function

##### $\exp{\left(x+y\right)}=\exp(x)\exp(y)$

This is the same thing as $e^{x+y}=e^xe^y$.

##### $\exp{x}>0$ when $x\in\mathbb{R}$

No matter what input you give it, you'll always get a positive number out of it.

Since $\exp{x}=\sum_{n=0}^{\infty}{\frac{x^n}{n!}}$, it's a sum of positive values, so it will always be positive when $x \ge 0$.

But for when $x<0$, we can say:
$$
1=\exp{\left(0\right)}=\exp{\left(x-x\right)}=\exp{\left(x\right)}\exp{\left(-x\right)}
$$
So if $\exp{\left(x\right)}\exp{\left(-x\right)}=1$, then $\exp{\left(x\right)}=\frac{1}{\exp{\left(-x\right)}}$.
And since $x<0$, $\exp{\left(-x\right)}$ will always be positive, therefore $\exp{x}>0$ for $x\in\mathbb{R}$.

##### The Inverse of $\exp x$

If $y=e^{x}$, then $x = \ln y$

##### $e^{g(x)}$ Differentiates to $g'(x)e^{g(x)}$

$$
\begin{align*}
f(x) &= e^{\sin x}\\
\\
\therefore f'(x) &= \cos(x) \cdot e^{\sin x}
\end{align*}
$$

##### $e^{x}$ grows faster than $x^{p}$ for any positive $p$

$$
\lim_{x \to \infty} \frac{x^{p}}{e^{x}} = 0 \quad \forall p>0
$$


---
### $exp(i\theta)$

The exponential function can be applied to an imaginary number.

$$\begin{aligned}
e^{i\theta}=\exp(i\theta)&=\sum_{n=0}^{\infty}\frac{(i\theta)^n}{n!} \\\\
&= 1+\frac{1}{1!}(i\theta)+\frac{1}{2!}(i\theta)^2+\frac{1}{3!}(i\theta)^3+\frac{1}{4!}(i\theta)^4+\dots \\\\
&=1+i\theta-\frac{1}{2}\theta^2-\frac{1}{6}i\theta^3+\frac{1}{24}\theta^4+\dots
\end{aligned}$$

So $\exp(i\theta)$ is generically a sum of complex numbers.

$$\begin{aligned}
\exp(i0)&=1 \\\\
\exp(i\theta)\exp(i\phi)&=\exp(i(\theta+\phi)) \\\\
\exp(in\theta)&=(\exp(i\theta))^n \\\\
\overline{\exp(i\theta)}&=\exp(-i\theta) \\\\
\left|\exp(i\theta\right)|&=1 \\\\
\end{aligned}$$

For any real $\theta$,
$$\begin{aligned}
z=e^{i\theta}&=\cos\theta+i\sin\theta \\\\
z=re^{i\theta}&=r(\cos\theta+i\sin\theta)
\end{aligned}$$

By showing that $e^{i\theta}=\cos\theta+i\sin\theta$ and $e^{-i\theta}=\cos\theta-i\sin\theta$, it can be shown by adding and subtracting both equations that:
$$\begin{aligned}
\cos\theta&=\frac{e^{i\theta}+e^{-i\theta}}{2} \\\\
\sin\theta&=\frac{e^{i\theta}-e^{-i\theta}}{2i}
\end{aligned}$$

And with this we can prove that $\cos^2\theta=\frac{1}{2}(1+\cos2\theta)$

$$\begin{aligned}
\cos^2\theta &=\left(\frac{e^{i\theta}+e^{-i\theta}}{2}\right)^2 \\\\
&=\frac{1}{4}\left(e^{2i\theta}+e^{-2i\theta}+2\right) \\\\
&=\frac{1}{4}\left(2\cos2\theta+2\right) \\\\
&=\frac{\cos2\theta+1}{2}
\end{aligned}$$

---
### $\exp(z)$

Let $z=x+iy$

$$\begin{aligned}
e^z=e^{x+iy}=e^xe^{iy}=e^x\left(\cos(y)+i\sin(y)\right)
\end{aligned}$$
Therefore $e^z$ has a modulus of $e^x$ and argument of $y$.

So from that we can determine:
$$\begin{aligned}
Re(\exp(z))&=e^x\cos(y) \\
Im(\exp(z))&=e^x\sin(y) \\
\left|\exp(z)\right|&=\exp(Re(z))=e^x \\
\arg(\exp(z))&=Im(z)=y \\
\overline{\exp(z)}&=\exp(\overline{z})
\end{aligned}$$
It's important to be able to derive these from the equation above.


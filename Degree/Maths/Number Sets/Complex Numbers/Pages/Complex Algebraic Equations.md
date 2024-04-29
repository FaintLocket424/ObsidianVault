---
tags:
  - degree/singlemathsa/numbersets/complexnumbers
---
![[Complex Numbers MOC 🌍]]
### Algebraic Equations

An algebraic equation for a complex variable $z$ is the same as a regular polynomial.
$$\begin{aligned}
az^n+bz^{n-1}+\dots+pz+q=0
\end{aligned}$$

---
### Degree One

$$\begin{aligned}
az+b=0\\\\
z=-\frac{b}{a}
\end{aligned}$$
gg ez no re

---
### Degree Two with real coefficients

$$\begin{aligned}
az^2+bz+c=0
\end{aligned}$$
With real coefficients $a$, $b$ and $c$. Multiplying the equation by $4a$ gives:
$$\begin{aligned}
4a^2z^2+4abz+4ac=0
\end{aligned}$$
Which can be rearranged to get
$$\begin{aligned}
(2az+b)^2=b^2-4ac
\end{aligned}$$
So, if the right hand side of the equation is positive, then we would get our regular 2 solutions. But in the case that $b^2-4ac<0$ there are no real solutions, only complex ones.
Therefore, if $b^2-4ac<0$
$$\begin{aligned}
2az+b=\pm i\sqrt{4ac-b^2}
\end{aligned}$$

So putting it all together:
$$z=\begin{cases}
\begin{aligned}
\frac{-b\pm\sqrt{b^2-4ac}}{2a}\quad\quad &b^2-4ac>0 \\
\frac{-b\pm i\sqrt{4ac-b^2}}{2a}\quad\quad &b^2-4ac<0 \\
\frac{-b}{2a}\quad\quad &b^2-4ac=0 \\
\end{aligned}\end{cases}$$

---
### $z^n=1$

We can use the polar representation $z=re^{i\theta}$ to solve.
$$\begin{aligned}
z^n=(re^{i\theta})^n=r^ne^{in\theta}&=1=1e^{i0} \\\\
r^ne^{in\theta}&=1e^{i0}
\end{aligned}$$
We can now match up the terms.
$$\begin{aligned}
r^n=1 \\\\
n\theta=0+2\pi k
\end{aligned}$$
That bottom term refers to how the argument can be a multiple of $2\pi$ and be the same value.

$r=1$ here.

$$\begin{aligned}
\theta=\frac{2\pi k}{n}
\end{aligned}$$

So then:
$$\begin{aligned}
z=\exp\left(i\frac{2\pi k}{n}\right)
\end{aligned}$$

So when $k=0$,
$$\begin{aligned}
z=\exp(0)=1
\end{aligned}$$
And when $k=n$,
$$\begin{aligned}
z&=\exp\left(i\frac{2\pi n}{n}\right) \\\\
z&=\exp\left(2\pi i\right)=1
\end{aligned}$$
So once $k$ gets above $n$, the outputs loop around back to 1. So even though there are infinite solutions, there are a limited number of unique solutions. These solutions are typically taken when $k=0,1,2,\dots,n-1$. So, the degree $n$ equation here has $n$ solutions.

$z^5=1$ has 5 solutions:
$$\begin{aligned}
z_0 &= 1 \\
z_1 &= \exp\left(\frac{2\pi i}{5}\right) \\
z_2 &= \exp\left(\frac{4\pi i}{5}\right) \\
z_3 &= \exp\left(\frac{6\pi i}{5}\right) \\
z_4 &= \exp\left(\frac{8\pi i}{5}\right) \\
\end{aligned}$$
And graphing these solutions gives us this fun picture:
![[Pasted image 20231031224139.png|600]]

---
### $z^n=a$ for $a\in\mathbb{C}$

We can write both complex numbers in their polar form.
$$\begin{aligned}
r^ne^{in\theta}=\rho e^{i\phi}
\end{aligned}$$

The matching up the modulus and arguments:
$$\begin{aligned}
r&=\sqrt[n]{\rho} \\\\\\
\theta&=\frac{\phi}{n}+\frac{2\pi k}{n}
\end{aligned}$$

So just like before, the unique solutions are when $k=0,1,2,\dots,n-1$
$$\begin{aligned}
z_0&=\sqrt[n]{\rho}\exp\left(i\left(\frac{\phi}{n}+\frac{2\pi k}{n}\right)\right)
\end{aligned}$$


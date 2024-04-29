---
tags:
  - degree/singlemathsa/numbersets/complexnumbers
---
![[Complex Numbers MOC 🌍]]
### Transcendental Equations

If $f(z)$ is not a finite degree polynomial or rational function then $f(z)=0$ is called a transcendental equation.
We do not know how many solutions a transcendental equation has.

---
### $e^z=1$

The only real solution to this is $z=0$, but there are more complex solutions.
$$e^z=e^xe^iy=1=1e^{i(0+2\pi k)}$$
Using this we can match up the modulus and argument.
$$\begin{aligned}
e^x&=1 \\
y&=0+2\pi k
\end{aligned}$$
Hence our solutions are $z=2k\pi i$ for all $k\in\mathbb{Z}$.

---
### $e^z=1+i$

First we rewrite the RHS in polar form with modulus $\sqrt{2}$ and argument $\frac{\pi}{4}+2\pi k$.

$$\begin{aligned}
e^xe^{iy}&=\sqrt{2}e^{i(\frac{\pi}{4}+2\pi k)}
\end{aligned}$$
Matching up the modulus and argument we get:
$$\begin{aligned}
e^x&=\sqrt{2} \\
y&=\frac{\pi}{4}+2\pi k
\end{aligned}$$
So $x=\frac{1}{2}\ln 2$.

So $z=\frac{1}{2}\ln 2+i\pi\left(2k+\frac{1}{4}\right)$

---
### $\sinh z=0$

$$\begin{aligned}
\frac{e^z-e^{-z}}{2}&=0 \\\\
e^{2z}&=1 \\\\
e^{2z}&=e^{2i\pi k}\quad\quad k\in\mathbb{Z} \\\\
2z&=2\pi ik \\
z&=\pi ik
\end{aligned}$$

---
### $\cos z=0$

$$\begin{aligned}
\frac{e^{iz}+e^{-iz}}{2}&=0 \\\\
e^{2iz}&=-1 \\\\
e^{2iz-i\pi}&=1 \\\\
2iz-\pi i&=2k\pi i \\\\
z&=\pi\left(k+\frac{1}{2}\right)\quad k\in\mathbb{Z}
\end{aligned}$$
This shows that $\cos z$ has no imaginary roots, it's just the regular roots we already know.
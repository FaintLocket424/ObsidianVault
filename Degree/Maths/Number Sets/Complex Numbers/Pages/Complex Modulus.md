---
tags:
  - degree/singlemathsa/numbersets/complexnumbers
---
![[Complex Numbers MOC 🌍]]
### The Modulus $\left|z\right|$
$$\begin{aligned}
r=|z|&=\sqrt{x^2+y^2} \\
&=\sqrt{Re(z)^2+Im(z)^2}
\end{aligned}$$
It's the modulus of $z$, or mod for short.

If you get a complicated number, you can use the formula
$$|z|^2=z\bar{z}$$
*Proof:*
$$\begin{aligned}
|z|^2&=\left(\sqrt{x^2+y^2}\right)^2 \\
&=x^2+y^2\\\\
z\bar{z}&=(x+iy)(x-iy) \\ 
&=x^2+y^2
\end{aligned}$$
---
### $\left|\frac{z}{w}\right|=\frac{|z|}{|w|}$

$$\begin{aligned}
\left|\frac{z}{w}\right|&=\left|\frac{z}{w}\frac{\bar w}{\bar w}\right| \\
&=\left|\frac{z\bar w}{\left|w\right|^2}\right| \\
&=\left|\left|z\bar w\right|\frac{1}{\left|w\right|^2}\right| \\
&=\frac{\left|z\bar w\right|}{\left|w\right|^2} \\
&=\frac{\left|z\right|\left|\bar w\right|}{\left|w\right|^2} \\
&=\frac{\left|z\right|\left|w\right|}{\left|w\right|^2} \\
&=\frac{\left|z\right|}{\left|w\right|}
\end{aligned}$$

E.g.
Find $Re(\frac{z}{w})$ in terms of $Re(z)$, $Re(w)$, $Im(z)$, $Im(w)$.

Let $z=x+iy$, $w=u+iv$

$$\begin{aligned}
\frac{z}{w}&=\frac{z\bar w}{\left|w\right|^2} \\\\
&=\frac{(x+iy)(u-iv)}{u^2+v^2} \\\\
&=\frac{xu+yv+i(...)}{u^2+v^2} \\\\
&=\frac{xu+yv}{u^2+v^2}+i(...) \\\\
&=Re\left(\frac{z}{w}\right)=\frac{xu+yv}{u^2+v^2} \\\\
&=\frac{Re(z)Re(w)+Im(z)Im(w)}{Re(w)^2+Im(w)^2}
\end{aligned}$$


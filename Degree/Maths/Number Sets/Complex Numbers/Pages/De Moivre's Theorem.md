---
tags:
  - degree/singlemathsa/numbersets/complexnumbers
---
![[Complex Numbers MOC 🌍]]
### De Moivre's

$$\begin{aligned}
\left(\cos{\theta}+i\sin{\theta}\right)^n=\cos(n\theta)+i\sin(n\theta)
\end{aligned}$$

While this is used for complex numbers, it can also be used for real numbers. For example, expressing $\cos3\theta$ as a polynomial in $\cos\theta$.

$$\begin{aligned}
\cos3\theta+i\sin3\theta&=(\cos\theta+i\sin\theta)^3
\end{aligned}$$
We can use the real part of this to get the answer.
$$\begin{aligned}
(\cos\theta+i\sin\theta)^3&=\cos^3\theta+3\cos^2\theta i\sin\theta+3\cos\theta i^2 \sin^2\theta+i^3\sin^3\theta \\\\
\therefore\cos3\theta&=\cos^3\theta-3\cos\theta\sin^2\theta \\
&=\cos^3\theta-3\cos\theta(1-\cos^2\theta) \\
&=4\cos^3\theta-3\cos\theta
\end{aligned}$$

Another example:
$$\begin{aligned}
(1+i)^{10} &= (\sqrt{2}(\cos\frac{\pi}{4}+i\sin\frac{\pi}{4}))^{10} \\
&=2^5(\cos\frac{\pi}{4}+i\sin\frac{\pi}{4})^{10} \\
&=2^5\left(\cos\frac{10\pi}{4}+i\sin\frac{10\pi}{4}\right) \\
&=32\left(\cos\frac{\pi}{2}+i\sin\frac{\pi}{2}\right) \\
&=32i
\end{aligned}$$


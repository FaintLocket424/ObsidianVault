---
tags:
  - degree/singlemathsa/trigonometry
---
![[Trigonometry MOC 🌍]]

### Sine and Cosine

Take a circle of radius $r$ and draw an arc of length $s$ in it at an angle $\theta$.

![[IMAGE arclength.png|350]]

Now consider the right angled triangle created by the angle within the circle.
![[IMAGE right angled triangle.png|350]]

We *define* the cosine and sine functions to be:
$$
\cos{\theta}=\frac{a}{r}
$$
$$
\sin{\theta}=\frac{b}{r}
$$
---
### The Tangent

$$
\frac{\sin{x}}{\cos{x}}=\tan{x}
$$
Literally that's it. What more do you want.

---
### Properties of the cosine and sine functions

We can use these definition to prove some properties of the cosine and sine functions.

#### $\cos^2{\theta}+\sin^2{\theta}\equiv1$ 

$a=r\cos{\theta}$ and $b=r\sin{\theta}$.
Using Pythagoras' theorem:
$$\begin{aligned}
a^2+b^2&=c^2 \\
\left(r\cos{\theta}\right)^2+\left(r\sin{\theta}\right)^2&=r^2 \\
r^2\cos^2{\theta}+r^2\sin^2{\theta}&=r^2 \\
\cos^2{\theta}+\sin^2{\theta}&\equiv1
\end{aligned}$$
---
#### $\cos{0}=1$, $\sin{0}=0$, $\cos{\frac{\pi}{2}}=0$, $\sin{\frac{\pi}{2}}=1$

If you think about the circle, this makes a lot of sense.
$\cos{0}$ and $\sin{0}$ means you have zero angle.
![[IMAGE Unit circle angle 0.png|350]]
And on the unit circle here where $r=1$, then $\cos{\theta}=a$ and $\sin{\theta}=b$. And $a$ is 1 and $b$ is 0.

With $\cos{\frac{\pi}{2}}=0$ and $\sin{\frac{\pi}{2}}=1$, we have a right angle.
![[IMAGE Unit circle right angle.png|350]]
So here, $a$ is 0 and $b$ is 1.
You get the idea.

---
#### $\cos{\left(-\theta\right)}=\cos{\theta}$, $\sin{\left(-\theta\right)=-\sin{\theta}}$

![[IMAGE Unit circle sin(-x) is -sin(x).png|350]]

When you go anti-clockwise, you keep $a$ but you flip $b$.
This gives you $\cos{\left(-\theta\right)}=\theta$ and $\sin{\left(-\theta\right)=-\sin{\theta}}$.

---
#### $\cos{\left(\theta+2\pi\right)}=\cos{\theta}$, $\sin{\left(\theta+2\pi\right)}=\sin{\theta}$

It's literally just going round the circle again you don't need me to explain this to you.

---
#### $\sin{\alpha}=\cos{\left(\alpha-\frac{\pi}{2}\right)}$ and $\cos{\alpha}=\sin{\left(\frac{\pi}{2}-\alpha\right)}$

These can be proven with the [[Trig Addition Formulae|Cosine Addition Formula]] and [[Trig Addition Formulae|Sine Addition Formula]].

$$\begin{aligned}
\cos{\left(\alpha-\frac{\pi}{2}\right)}&=\cos{\alpha}\cos{\frac{\pi}{2}}+\sin{\alpha}\sin{\frac{\pi}{2}} \\
&=(0)\cos{\alpha}+(1)\sin{\alpha} \\
&=\sin{\alpha}
\end{aligned}$$
And
$$\begin{aligned}
\cos{\alpha}&=\sin{\left(\frac{\pi}{2}-\alpha\right)} \\\\
&=\sin{\frac{\pi}{2}}\cos{\alpha}-\cos{\frac{\pi}{2}}\sin{\alpha} \\\\
&=(1)\cos{\alpha}-(0)\sin{\alpha} \\\\
&=\cos{\alpha}
\end{aligned}$$

---
### $\cos(z)$ and $\sin(z)$

Let $z=x+iy$

$$\begin{aligned}
\cos(z)&=\frac{e^{iz}+e^{-iz}}{2} \\\\
\sin(z)&=\frac{e^{iz}-e^{-iz}}{2i} \\\\
\cosh(z)&=\frac{e^{z}+e^{-z}}{2} \\\\
\sinh(z)&=\frac{e^{z}-e^{-z}}{2} \\\\
\end{aligned}$$

We can show that for any complex number $z$ that:
$$\begin{aligned}
\cos(iz)&=\cosh(z) \\
\sin(iz)&=i\sinh(z) \\
\cosh(iz)&=\cos(z) \\
\sinh(iz)&=i\sin(z)
\end{aligned}$$

Using that we can get the real and imaginary components of $sin(z)$.
$$\begin{aligned}
\sin(z)&=\sin(x+iy) \\
&=\sin(x)\cos(iy)+\cos(x)\sin(iy) \\
&=\sin(x)\cosh(y)+i\cos(x)\sinh(y) \\\\
\therefore Re(\sin z)&=\sin(x)\cosh(y) \\
Im(\sin z)&=\cos(x)\sinh(y)
\end{aligned}$$

And we can get $\left|\sin(z)\right|$
$$\begin{aligned}
\left|\sin(z)\right|^2&=\left(\sin(x)\cosh(y)\right)^2+\left(\cos(x)\sinh(y)\right)^2 \\
&=\sin^2x(1+\sinh^2y)+\cos^2x\sinh^2y \\
&=\sin^2x+(\sin^2x+\cos^2x)\sinh^2y \\
&=\sin^2x+\sinh^2y \\\\
\therefore \left|\sin z\right|&=\sqrt{\sin^2x+\sinh^2y}
\end{aligned}$$


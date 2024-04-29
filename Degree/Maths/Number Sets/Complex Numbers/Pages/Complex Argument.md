---
tags:
  - degree/singlemathsa/numbersets/complexnumbers
---
![[Complex Numbers MOC 🌍]]
### The Argument, $\theta$

For a complex number $z$, we define the argument of $z$, denoted as $\theta=arg(z)$, as the angle between the $x$-axis and the line from 0 to $z$, measured anti-clockwise.

This is basically just polar co-ordinates lol.

![[IMAGE Complex Argument.png|550]]

The argument is only defined up to $2\pi$ since that would just be going all the way round the circle and it would be $0$.

$arg(1+i)=\frac{\pi}{4}$

$arg(-3)=\pi$

$arg(-2i)=\frac{3\pi}{2}=-\frac{\pi}{2}$

$$\begin{aligned}
\tan(\arg(z))=\frac{Im(z)}{Re(z)}
\end{aligned}$$
---
### Getting Trolled by $\tan{\theta}$

If you have the complex number $z=1+i$, then $\tan{\theta}=1$, therefore $\theta=\frac{\pi}{4}$.

But if you have $z=-1-i$, then $\tan{\theta}=1$, but $\theta=-\frac{3\pi}{4}$.

![[IMAGE argand diagram.png]]

You can circumvent this by just drawing the argand diagram.

---
$\arg(\overline{z})=-\arg(z)$ 

![[Pasted image 20231024171712.png]]

---
$\arg(-z)=\pi+arg(z)$

![[Pasted image 20231024171813.png]]

---
$\arg(az)=\begin{cases}\arg(z)\quad a>0\\\pi+\arg(z)\quad a<0\end{cases}$

$a$ is just a real scalar and the length of a vector does not change it's length (if you think of complex numbers as vectors on the argand plane).

---
### The Polar Representation

$$z=r(\cos(\theta)+i\sin(\theta))$$
This is the polar representation of $z$.

It tells you immediately what $\left|z\right|$ and $\arg(z)$ are.

Examples:

$$\begin{aligned}
z_1&=1-\sqrt{3}i \\\\
|z_1|&=\sqrt{1^2+3}=2 \\
\arg(z_1)&=\arctan(-\sqrt{3})=-\frac{\pi}{3} \\\\
z_1&=2\left[\cos\left(-\frac{\pi}{3}\right)+i\sin\left(-\frac{\pi}{3}\right)\right]
\end{aligned}$$

$$\begin{aligned}
z_2&=17\left[\sin\left(\frac{\pi}{4}\right)+i\cos\left(\frac{\pi}{4}\right)\right] \\\\
&=17\left[\cos\left(\frac{\pi}{2}-\frac{\pi}{4}\right)+i\sin\left(\frac{\pi}{2}-\frac{\pi}{4}\right)\right] \\\\
&=17\left[\cos\left(\frac{\pi}{4}\right)+i\sin\left(\frac{\pi}{4}\right)\right]
\end{aligned}$$


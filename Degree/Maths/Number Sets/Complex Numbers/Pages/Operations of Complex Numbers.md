---
tags:
  - degree/singlemathsa/numbersets/complexnumbers
---
![[Complex Numbers MOC 🌍]]

### Expression
Complex Numbers $\mathbb{C}$ are numbers expressed in the form $a+bi$ where $a,b\in\mathbb{R}$

---
### Plotting:
*To every point $(x,y)$ in the plane, we associate a complex number $x+iy$*

This is the complex or argand plane.

![[IMAGE Complex Numbers plotted on the complex plane.png]]

---
### Operations
Just treat $i$ as a variable and it all works fine.
Also, $i^2=-1$
##### Addition
$(3+4i)+(-6+2i)=3-6+(4+2)i=-3+6i$

##### Subtraction
$\pi+2i-(3+\sqrt{7}i)=3+\pi+(2+\sqrt{7})i)$

##### Multiplication
$(1+i)(2+i)=2+2i+i+i^2=2+3i-1=1+3i$

##### Division
###### Division by a real number:
$$\frac{a+bi}{c}=\frac{a}{c}+\frac{bi}{c}$$
###### Division by a complex number:
It's literally just rationalising the denominator.
$$\begin{aligned}
\frac{z}{w}&=\frac{z}{w}\frac{\bar w}{\bar w}=\frac{z\bar w}{|w|^2} \\\\
\frac{1-2i}{3+4i}&=\frac{1-2i}{3+4i}\times\frac{3-4i}{3-4i} \\ \\
&=\frac{(1-2i)(3-4i)}{9-16i^2} \\\\
&=\frac{3-4i-6i+8i^2}{9+16} \\\\
&=\frac{-5-10i}{25} \\\\
&=-\frac{1}{5}-\frac{2}{5}i
\end{aligned}$$
---
### Complex Numbers as Variables
Usually $z$ or $w$ are used for complex numbers, just because.

If $z=x+iy$ and $w=u+iv$ then $zw=(x+iy)(u+iv)$.

E.g.
$z=3-4i$
$w=3-i$

Calculate $z-w$, $zw$ and $z^3$:
$$\begin{aligned}
z-w&=3-4i-3+i=-3i \\
zw&=(3-4i)(3-i)=9-3i-12i+4i^2=5-15i
\end{aligned}$$
And for $z^3$:
$$\begin{aligned}
z^3&=(3-4i)^3 \\
&=(3-4i)(9-24i+16i^2) \\
&=(3-4i)(-7-24i) \\
&=-27-72i+28i+96i^2 \\
&=-123-44i
\end{aligned}$$
---
### The Case of $\frac{1}{i}$

$$\begin{aligned}
\frac{1}{i}&=\frac{1}{i}\times\frac{-i}{-i} \\\\
&=\frac{-i}{-(i)^2} \\\\
&=\frac{-i}{1}=-i
\end{aligned}$$

So $\frac{1}{i}$ is $-i$. Just deal with it lol.

---
### $Re(z)$ and $Im(z)$

Let $z=x+iy$ where $z\in\mathbb{C}$

So:
$Re(z)=x=\left|z\right|\cos(\arg(z))$
$Im(z)=y=|z|\sin(\arg (z))$

It's literally just getting that component of the number.

If $Im(z)=0$ then $z$ is called real. (Even though it's still a complex number)

If $Re(z)=0$ then $z$ is called (purely) imaginary

If you get a complicated number, you can use the formulae
$$\begin{aligned}
Re(z)&=\frac{1}{2}(z+\bar{z}) \\
Im(z)&=\frac{1}{2i}(z-\bar{z})
\end{aligned}$$
*Proof:*
$$\begin{aligned}
Re(z)&=x \\\\
Re(z)&=\frac{1}{2}\left(x+iy+z-iy\right) \\
Re(z)&=\frac{1}{2}\times2x \\
Re(z)&=x
\end{aligned}$$
And for the $Im(z)$:
$$\begin{aligned}
Im(z)&=z \\\\\\
Im(z)&=\frac{1}{2i}\left(x+iy-x+iy\right) \\
Im(z)&=\frac{1}{2i}\times2iy \\
Im(z)&=y
\end{aligned}$$


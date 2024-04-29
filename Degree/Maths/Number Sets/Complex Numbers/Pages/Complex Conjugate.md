---
tags:
  - degree/singlemathsa/numbersets/complexnumbers
---
![[Complex Numbers MOC 🌍]]
### The Complex Conjugate $\bar{z}$ or $z^*$

$$\begin{aligned}
z&=x+iy \\
\bar{z}&=x-iy
\end{aligned}$$
The complex conjugate of $z$.
It's a reflection in the $x$ axis of an argand diagram.
![[IMAGE Complex Conjugate.png]]

$$\begin{aligned}
z&=x+iy \\
w&=u+iv \\
\\
\overline{z+w}&=\overline{x+iy+u+iv} \\
&=\overline{x+u+i(y+v)} \\
&=x+u-i(y+v) \\\\
\bar{z}+\bar{w}&=x-iy+u-iv \\
&=x+u-i(y+v)
\end{aligned}$$
---
$$\begin{aligned}
\overline{zw}&=\overline{(x+iy)(u+iv)} \\
&=\overline{xu-yv+i(yu+xv)} \\
&=xu-yv-i(yu+xv) \\\\
\bar z\times \bar w&=(x-iy)(u-iv) \\
&=xu+i^2yv-iyu-ixv \\
&=xu-yv-i(yu+xv)
\end{aligned}$$
---
$$\begin{aligned}
|zw|&=|z||w|
\end{aligned}$$
We know from before that $|z|^2=z\bar{z}$ so:
$$\begin{aligned}
|zw|^2&=|zw||\overline{zw}| \\
&=z\bar z w \bar w \\
&=|z|^2|w|^2
\end{aligned}$$
Now take the square root of both sides. We can do this since the mod function is always positive.
$$\begin{aligned}
|zw|&=|z||w| \\
\end{aligned}$$
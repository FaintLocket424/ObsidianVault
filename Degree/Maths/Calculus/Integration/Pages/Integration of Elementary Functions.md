---
tags:
  - degree/singlemathsa/integration
  - degree/mathsforcs/calculus/integration
---
![[Integration MOC 🌍]]

$$
\begin{align*}
\int a &= ax + c\\
\\
\int x^{n} (n \ne -1) &= \frac{x^{n+1}}{n+1} + c\\
\\
\int x^{-1} &= \ln |x| + c\\
\\
\int e^{ax} &= \frac{1}{a} e^{ax} +c\\
\\
\int \sin(ax) &= - \frac{1}{a} \cos(ax) + c\\
\\
\int \cos(ax) &= \frac{1}{a} \sin(ax) + c\\
\\
\int \sinh(ax) &= \frac{1}{a} \cosh(ax) + c\\
\\
\int \cosh(ax) &= \frac{1}{a} \sinh(ax) + c
\end{align*}
$$
A significant amount of this is about being able to recognise the derivatives of functions.

Many complex antiderivatives can be derived from a knowledge of derivatives:
$$
\int \frac{1}{\sqrt{a^{2} - x^{2}}} dx = \arcsin\left(\frac{x}{a}\right) + c
$$
We get this from knowing that 
$$
\frac{d(\arcsin x)}{dx} = \frac{1}{\sqrt{1-x^{2}}}
$$
And 
$$
\int \sec x \tan x dx = \sec x + c
$$
Since $\sec x = \frac{1}{\cos(x)}$ and $\tan x = \frac{\sin x}{\cos x}$

---
### Additional Information

- [Wikipedia]
- [[Maths for CS Calculus Topic 13 Integration Part 1.pdf]]
- [[Maths for CS Calculus Topic 13 Integration Part 2.pdf]]
- [Maybe Practical Q and As]

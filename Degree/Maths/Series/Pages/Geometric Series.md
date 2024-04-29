---
tags:
  - degree/singlemathsa/series
---
![[Series MOC 🌍]]

A series where $a_{n} = a x^{n}$ for some $a\ne 0$ and $x\in\mathbb{R}$.
$$
\begin{align*}
S_{N} &= \sum^{N-1}_{n=0}ax^{n}=a + ax + ax^{2} + \dots + ax^{N-1}\\
x S_{N} &= ax + ax^{2} + \dots + ax^{N-1} + ax^{N}\\
xS_{N} &= S_{N}-a+ax^{N}\\
(1-x)S_{N} &= a(1-x^{N})\\
\\
S_{N} &= a \frac{1-x^{N}}{1-x} \quad \text{if $|x|<1$}
\end{align*}
$$

If $|x|<1$ then $x^{N}\rightarrow 0$ as $N \rightarrow \infty$ and $S_{N}\rightarrow \frac{a}{1-x}$.

If $|x|\ge 1$ then the series is divergent.
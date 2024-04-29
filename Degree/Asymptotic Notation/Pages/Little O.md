---
tags:
  - degree/ads/asymptoticnotation
---
![[Asymptotic Notation MOC 🌍]]

### Little-O

Little-O is a tool for disregarding "small order" terms.

We say that $f(x)$ is $o(g(x))$ when
$$\begin{aligned}
\lim_{x\rightarrow\infty}\frac{f(x)}{g(x)}=0
\end{aligned}$$
As $x$ gets infinitely large, $\frac{f(x)}{g(x)}\rightarrow 0$


Also, if $f(x)$ is $o(g(x))$ implies $f(x)$ is $O(g(x))$

---
### Sublinear Functions

A sublinear function is one that grows slower than any linear function.

A function $f(x)$ is called sublinear if $f(x)$ is $o(x)$.
$$\begin{aligned}
\lim_{x\rightarrow\infty}\frac{f(x)}{x}=0
\end{aligned}$$

If we take the function $f(x)=\frac{100}{\log x}$, we can show it's sublinear since
$$\begin{aligned}
\lim_{x\rightarrow\infty}\frac{f(x)}{x}=\lim_{x\rightarrow \infty}\frac{100}{x\log x}=0
\end{aligned}$$

But a function like $f(x)=\frac{1}{2}x$ is not sublinear because
$$\begin{aligned}
	\lim_{x\rightarrow \infty}\frac{f(x)}{x}=\lim_{x\rightarrow\infty}\frac{x}{2x}=\frac{1}{2}
\end{aligned}$$

But a function like $f(x)=\sqrt[3]{x^2}$  is sublinear because
$$\begin{aligned}
	\lim_{x\rightarrow \infty}\frac{f(x)}{x}=\lim_{x\rightarrow\infty}\frac{x^{\frac{2}{3}}}{x}=\lim_{x\rightarrow\infty}x^{-\frac{1}{3}}=0
\end{aligned}$$

---
### Some General Rules

If $f_1(x)$ is $o(g(x))$ and $f_2(x)$ is $o(g(x))$, then $f_1(x)+f_2(x)$ is $o(g(x))$

If $f_1(x)$ is $\mathcal{O}(g(x))$ and $f_2(x)$ is $o(g(x))$, then $f_1(x)+f_2(x)$ is $\mathcal{O}(g(x))$

If $f_1(x)$ is $\Theta(g(x))$ and $f_2(x)$ is $o(g(x))$, then $f_1(x)+f_2(x)$ is $\Theta(g(x))$

GENERAL RULE: If you add a term to a function that has the same little-o, then it will not affect the $o$, $\mathcal O$, or $\Theta$ of the original function. 